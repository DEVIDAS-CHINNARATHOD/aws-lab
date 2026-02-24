# Working with Amazon DynamoDB

Explanation and Hands-on Labs

------------------------------------------------------------------------

## 1. Introduction to Amazon DynamoDB

Amazon DynamoDB is a fully managed NoSQL database service provided by
AWS. It supports key-value and document data models and is designed for
high performance, scalability, and low latency.

### Key Features

-   Fully managed and serverless
-   Single-digit millisecond latency
-   Automatic scaling
-   On-demand billing option
-   Built-in security and backup

------------------------------------------------------------------------

## 2. Core Concepts

### Table

A collection of items.

### Item

A single record in a table (stored in JSON-like format).

### Attribute

A property of an item (similar to a column in relational databases).

### Partition Key

The primary key used to uniquely identify each item.

### Sort Key

Optional key used with partition key to enable range queries.

### Global Secondary Index (GSI)

Allows querying using non-primary key attributes.

### Local Secondary Index (LSI)

Alternate sort key with same partition key.

### RCU / WCU

Read Capacity Units and Write Capacity Units.

### TTL (Time To Live)

Automatically deletes expired items.

------------------------------------------------------------------------

# LAB 1: Creating and Using a DynamoDB Table

## Objective

Create a table and perform CRUD operations.

## Scenario

Student Management System

## Steps

1.  Login to AWS Console.
2.  Navigate to DynamoDB.
3.  Click "Create Table".
4.  Enter:
    -   Table name: Students
    -   Partition key: student_id (String)
5.  Select Billing mode: On-Demand.
6.  Click Create.

## Insert Item

Go to Explore Table → Create Item → JSON view and insert:

{ "student_id": "S101", "name": "Devidas", "branch": "CSE", "semester":
4, "cgpa": 8.7 }

## Perform Operations

-   Get Item
-   Update Item (modify CGPA)
-   Delete Item

## Learning Outcome

-   Understand DynamoDB data model
-   Perform basic CRUD operations

------------------------------------------------------------------------

# LAB 2: Query vs Scan and Indexing

## Objective

Understand performance difference between Query and Scan.

## Scenario

Query students by branch.

## Steps

1.  Open Students table.
2.  Go to Indexes → Create Index.
3.  Create Global Secondary Index:
    -   Index name: branch-index
    -   Partition key: branch (String)
4.  Create index.

## Perform Query

Use Query operation: branch = "CSE"

## Compare

  Operation   Performance   Cost
  ----------- ------------- ------
  Scan        Slow          High
  Query       Fast          Low

## Learning Outcome

-   Understand why Scan is inefficient
-   Learn to optimize using GSI

------------------------------------------------------------------------

# LAB 3: TTL and Streams (Advanced)

## Objective

Implement auto-expiry and event-driven processing.

## Scenario

Session or OTP storage system.

## Steps

1.  Create new table:
    -   Table name: UserSessions
    -   Partition key: session_id (String)
    -   Billing mode: On-Demand
2.  Insert Sample Item:

{ "session_id": "abc123", "user": "devidas", "expiry_time": 1735689600 }

3.  Enable TTL:
    -   Go to Additional Settings → Time to Live
    -   Enable TTL
    -   TTL attribute name: expiry_time
4.  Enable DynamoDB Streams:
    -   Go to Exports and Streams
    -   Enable Streams
    -   Select New and Old Images
5.  (Optional) Connect AWS Lambda to process stream events.

## Learning Outcome

-   Understand TTL functionality
-   Learn event-driven architecture using Streams
-   Integrate DynamoDB with Lambda

------------------------------------------------------------------------

# Performance Monitoring

Use Amazon CloudWatch to monitor: - Read latency - Write latency -
Consumed capacity

------------------------------------------------------------------------

# Suggested Architecture

Client → API → DynamoDB → Streams → Lambda → Logs

------------------------------------------------------------------------

End of Document
