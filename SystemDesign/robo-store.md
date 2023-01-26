# Case Study - Ecommerce Robo Shop

## Things to cover

- Technology architecture / Blueprint
- Technology lists, Tools, Products, Code repository tools
- ER Diagram, High level process flow diagram
- One module detailed design diagram
- Recommendation on Security & Data Encryption Implementation
- Deployment Diagram
- Devops recommendations
- Ball park effort estimtes (hours) & approach

## Overview

### Use cases

- Types of users
    1. General Public/ Customers
    2. Merchants/Vendors
    3. System Admins
- Registration of Users
- Profile Management of Users
- Search for products
- Create and manage shopping cart
- Notifiy customers about Offers
- Uploading most purchased items (why is this?)
- Data and graphs for Admins
- Data and graphs for vendors
- Feedback Mechanism
- Payment Mechanism
- Product recommendation

### Out of Scope

- Shipping

### Who will use

- Guest
- Registered Customers
- Merchants/Vendors
- System Admins

### How many will use

- Amazon has 300 million customer accounts and 1.9 million selling partners

### Usage Patterns

## General Notes
- This case study is similar to Shopify.
- Use cases of ML at Shopify
    - Internal use cases
        1. Fraud detection
        2. Revenue Prediction
    - External use cases
        1. [Product Categorization](https://shopify.engineering/using-rich-image-text-data-categorize-products)
        2. [Recommendation System](https://shopify.engineering/evaluating-search-algorithms)
        3. [Demand forecasting](https://www.amazon.science/blog/data-on-correlated-products-and-sellers-helps-improve-demand-forecasting)
- [Apache Airflow](https://airflow.apache.org/docs/apache-airflow/stable/) is a batch workflow orchestration platform. Airflow's philosophy is to defien workflow's as code, so coding will always be required.
- [Oozie](https://oozie.apache.org/) is a workflow scheduler system for managing Apache Hadoop jobs.
- SCIM - System for Cross-domain Identity Management
