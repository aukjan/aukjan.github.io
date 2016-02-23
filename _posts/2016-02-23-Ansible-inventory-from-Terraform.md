---
layout: post
title: Ansible inventory generated from Terraform.
excerpt_separator: <!--more-->
---

When creating an infrastructure with [Terraform](http://terraform.io), it is nice to have Terraform create the [Ansible](https://www.ansible.com) inventory file for us. To achive this it is possible to utilize the Terraform templates for generation of hostnames and the actual inventory file. All code can be found [here](https://github.com/aukjan/terraform-playground/tree/master/ansible/hosts)


<!--more-->

## The Templates

First we create the template for our hostnames following our naming convention:

~~~~
${name}-${env}-${format("%02s",index)} ${extra}
~~~~

Next we create the template for our Ansible inventory, where in this case we only have one set of hosts, and we utilize grouping of those hosts under a `production` group. This allows us to specify environment specific variables via group vars. 

~~~
[web]
${web_hosts}

[${env}:children]
web
~~~

## Terraform file

In our terraform file we use two `template_file` definitions to generate both the hostnames and the ansible inventory. In this example we 'fake' the IP's by defining a list, but in real life this would be a list of ipadresses from a resource (e.g. `aws_instance`). 

~~~ 
variable "web_ips"  { default = "10.0.0.1,10.0.0.2,10.0.0.3" }

resource "template_file" "web_ansible" {
  count = "${length(split(",",var.web_ips))}"
  template = "${file("${path.module}/hostname.tpl")}"
  vars {
    index = "${count.index + 1}"
    name  = "web"
    env   = "p"
    extra = " ansible_host=${element(split(",",var.web_ips),count.index)}"
    # extra = ""
  }
}

resource "template_file" "ansible_inventory" {
  template = "${file("${path.module}/ansible_inventory.tpl")}"
  vars {
    env         = "production"
    web_hosts   = "${join("\n",template_file.web_ansible.*.rendered)}"
  }
}

output "ansible_inventory" {
	value = "${template_file.ansible_hosts.rendered}"
}
~~~


## Execution and Result

Now applying the terraform file, and calling the 'output' command from terraform we can create our inventory:

~~~
$ terraform apply 
$ terraform output ansible_inventory > inventory
~~~

giving the following result:

~~~
$ cat inventory
[web]
web-p-01  ansible_host=10.0.0.1
web-p-02  ansible_host=10.0.0.2
web-p-03  ansible_host=10.0.0.3

[production:children]
web

~~~
