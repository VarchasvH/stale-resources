# AWS Cloud Cost Optimization Project - Managing Stale Resources
In this example, we'll create a Lambda function that identifies EBS snapshots that are no longer associated with any active EC2 instance and deletes them to save on storage costs.

---

## Situation
A Developer named John was using an EC2 instance and he created many Snapshots (Backups) for the instance that he wanted to use later. But, after he was done using that instance, he terminated it and deleted the volumes but he did not delete the Snapshots for it and overtime the charges from them began pour in and the company is now unable to figure out the problem. 


**Now, As a DevOps Engineer, it is our responsibility to figure out the problem.**

### Solution
We will create a Lambda function that fetches all EBS snapshots owned by the same account ('self') and also retrieves a list of active EC2 instances (running and stopped). For each snapshot, it checks if the associated volume (if exists) is not associated with any active instance. If it finds a stale snapshot, it deletes it, effectively optimizing storage costs.

---
