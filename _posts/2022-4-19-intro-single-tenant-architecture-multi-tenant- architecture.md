---
title: An intro about single tenant architecture & multi tenant architecture
layout: post
tags:
  - SaaS
  - Application Architecture
---

A single-tenant architecture (siloed model) is a single architecture per organization where the application has its own infrastructure, hardware, and software ecosystem.

Multi tenant architecture is an ecosystem or model, in which a single environment can serve multiple tenants utilizing a scalable, available, and resilient architecture. The infrastructure is completely shared, logically isolated, and with fully centralized services.

### Types of Multi tenant SaaS architectures

1. Application layer Multi-tenancy
2. Database layer Multi-tenancy

## Application layer Multi-tenancy

#### Examples

1. Monolithic architecture for SaaS
2. Microservices Architecture for SaaS with containers
3. Kubernetes Architecture for SaaS
4. Serverless Architecture for SaaS


## Database Layer Multi-tenancy

When choosing database architecture, there are multiple criterias to assess. The criterias are Scalability (Number of tenants, storage per-tenant, workload), Tenant isolation, database costs (per tenant costs), development complexity (changes in schemas, queries, etc.), and operational complexity (Database clustering, update tenant data, database administration, and maintenance).

#### Examples

### 1. Single database: A table per tenant

Known as DB pooled model.

It consists of leveraging a table per each organization within a database schema. Every table name has its own tenantID, which is very straightforward to design and architect.

#### Pros

1. Easy to scale
2. Great for thousands of tenant

#### Cons

1. Difficult for backup & recovery
2. Poor data isolation
3. Performance degradation (one tenant can overuse compute and ram resources from another)

### 2. Single Database: A schema per tenant

Known as the bridge model.

If there is more than 100 schemas or tenants within a database, it can provoke a lag in database performance. Hence, it is recommended to split the database into two (add the second database as a replica). The best database tool for this approach is PostgreSQL, which supports multiple schemas without much complexity. This strategy shares resources, compute, and storage across all its tenants.

#### Pros

1. Less development complexity
2. Secure than DB pooled model
3. Can customize schemas per tenant

#### Cons

1. This architecture not comply with PCI / HIPPA / FedRamp regulations
2. Medium tenent isolation

### 3. Database Server Per Tenant

Also known as Siloed model.

Now we need a database instance per customer. Expensive, but the best for isolation and security compliance.

#### Pros

1. High data isolation
2. Widely used and accepted

#### Cons

1. More cost
2. Complex to manage dozens DB server
