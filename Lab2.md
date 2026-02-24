# Experiment Title  
**2)Orchestrating Serverless Functions with AWS Step Functions**

---

## Aim  
To orchestrate serverless functions using AWS Step Functions.

---

## Objectives / What You Will Learn  
- Create AWS Lambda functions  
- Orchestrate Lambda functions using AWS Step Functions  
- Understand state machines, execution flow, and outputs  
- Learn industry-relevant serverless architecture  

---

## Architecture  
AWS Step Functions
↓
Lambda Function 1 (HelloFunction)
↓
Lambda Function 2 (ProcessFunction)


- No EC2 instances  
- Fully serverless architecture  

---

## Services Used  
- **AWS Step Functions**  
- **AWS Lambda**  
- **IAM** (auto-created roles)  

**Cost:** Very low (few cents, covered by credits)

---

## Procedure  

### Step 1: Create First Lambda Function (HelloFunction)

1. Login to AWS Management Console  
2. Navigate to **AWS Lambda**  
3. Click **Create function**  
4. Select **Author from scratch**  
5. Enter:
   - Function name: `HelloFunction`  
   - Runtime: Python 3.12  
6. Click **Create function**  
7. Replace the default code with:

```python
def lambda_handler(event, context):
    return {
        "message": "Hello from Lambda",
        "input": event
    }
```

Click Deploy

Click Test → Create test → Test

Verify successful execution

### Step 2: Create Second Lambda Function (ProcessFunction)

Create another Lambda function

Function name: ProcessFunction

Runtime: Python 3.12

Use the following code:
```
def lambda_handler(event, context):
    return {
        "status": "Processed successfully",
        "previous": event
    }
```
Click Deploy

Test the function

### Step 3: Create Step Functions State Machine

Navigate to AWS Step Functions

Click Create state machine

Choose Visual workflow

Click Next

Drag Lambda Invoke state twice

Configure:

First state → HelloFunction

Second state → ProcessFunction

Connect the states sequentially

Click Next

Enter:

State machine name: ServerlessWorkflow

Select Create new role

Click Create state machine

### Step 4: Start Execution

Open the state machine ServerlessWorkflow

Click Start execution

Enter input:

{
  "name": "AWS Lab"
}

Click Start execution

Observe execution flow turning green

### Step 5: View Output

Click the final state in the execution graph

Observe the JSON output

Verify Lambda function chaining

### Step 6: Cleanup (Important)

Delete the Step Functions state machine

Delete both Lambda functions

This avoids unnecessary usage and saves credits.

Result

The serverless workflow was successfully executed using AWS Step Functions, demonstrating orchestration of multiple AWS Lambda functions.

Conclusion

AWS Step Functions enables efficient orchestration of serverless applications by coordinating multiple AWS Lambda functions without managing servers. This experiment demonstrates a scalable and cost-effective serverless workflow architecture.

