# AWS Cloud Cost Optimization Project - Managing Stale Resources
In this example, we'll create a Lambda function that identifies EBS snapshots that are no longer associated with any active EC2 instance and deletes them to save on storage costs.

---

# Scenario
A Developer named John was using an EC2 instance and he created many Snapshots (Backups) for the instance that he wanted to use later. But, after he was done using that instance, he terminated it and deleted the volumes but he did not delete the Snapshots for it and overtime the charges from them began pour in and the company is now unable to figure out the problem. 


**Now, As a DevOps Engineer, it is our responsibility to figure out the problem.**

## Solution
We will create a Lambda function that fetches all EBS snapshots owned by the same account ('self') and also retrieves a list of active EC2 instances (running and stopped). For each snapshot, it checks if the associated volume (if exists) is not associated with any active instance. If it finds a stale snapshot, it deletes it, effectively optimizing storage costs.

---

# Step-by-Step Tutorial
1. Create a new EC2 instance with the free-tier configurations.

2. Create a Snapshot of this new instance.

3. Create a Lambda function with the Python language.

4. Copy the Python script from this repository and paste it in the function code.

5. Go to Configuration -> General Configuration -> Edit and change the timeout to 10s.

6. To Add the required permissions, Go to Configuration -> Permissions, and click on the role name.

7. On the new page, Create two new Policies with the following permissions:
    * 'DescribeSnapshots' and 'DeleteSnapshots'.
    * 'DescribeInstances' and 'DescribeVolumes'

8. Attach these new Policies to our role.

9. Now Deploy the code on the Lambda function and click on test. It should run successfully.

10. But you will notice that the Snapshot is not deleted yet, For the program to run correctly we need to terminate the EC2 instance first.

11. After you terminate the instance, Test the Lambda Code again and now it will delete this snapshot.

![Screenshot 2023-08-12 145618](https://github.com/VarchasvH/stale-resources/assets/100064742/c1f9c20c-4418-4890-a346-30c0914ba9bb)

---











 


