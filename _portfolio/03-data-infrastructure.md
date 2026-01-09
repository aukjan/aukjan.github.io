---
layout: portfolio
title: "Real-Time Data Infrastructure"
date: 2021-09-01
role: "Engineering Manager"
company_context: "B2B SaaS Platform (Series A, 30-person team)"
category: technical
summary: "Built real-time data pipeline enabling customer analytics dashboards, reducing data latency from hours to seconds while processing 10M+ events daily."
---

## The Context

[Placeholder: B2B SaaS platform generating massive event data but unable to provide real-time insights. Customers requesting live analytics dashboards for their business decisions. Existing batch ETL processes running nightly, 12+ hour data lag. Competitive pressure from platforms offering real-time capabilities.]

## The Challenge

[Placeholder: Legacy batch processing inadequate for real-time needs. No streaming infrastructure in place. Small team with no prior experience building data pipelines. Budget constraints limiting infrastructure spending. Need to maintain existing analytics while building new system. Can't afford data loss during migration.]

## Your Approach

[Placeholder: Evaluated streaming platforms (Kafka, Kinesis, Pub/Sub). Started with managed services to minimize operational burden. Built event schema registry for data consistency. Implemented dual-write pattern for safe migration. Created self-service dashboard builder for customers. Phased rollout starting with non-critical data streams.]

## Key Decisions

[Placeholder: Key decision 1 - Chose managed cloud services (AWS Kinesis) over self-hosted Kafka to focus team on business logic. Key decision 2 - Built abstractions allowing pipeline logic changes without customer impact. Key decision 3 - Invested in monitoring and alerting from day one.]

## The Outcome

[Placeholder: Real-time analytics platform launched in 5 months. Processing 10M+ events per day with <5 second latency. Customer satisfaction scores improved 35%. New feature became key differentiator in sales. Platform scaled to 50M+ events/day without major changes. Team gained valuable distributed systems experience.]

## What You Learned

[Placeholder: Managed services accelerate delivery for small teams. Clear schemas and contracts prevent data quality issues. Monitoring is not optional for distributed systems. Phased rollouts reduce risk significantly. Build for the scale you need tomorrow, not 10x beyond it.]
