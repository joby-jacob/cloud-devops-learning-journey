# IAM Users, Groups, and Policies

## IAM User
An IAM User is a permanent identity used by a person or service to log in to AWS.  
Users can authenticate using a password (Console) or access keys (CLI).

## IAM Group
An IAM Group is a collection of IAM Users.  
Permissions are assigned to the group, and all users in the group inherit those permissions.  
This allows easier and consistent access management.

## IAM Policy
An IAM Policy is a JSON document that defines *what actions are allowed or denied* in AWS.  
Policies can be attached to Users, Groups, or Roles.

## Why Groups Are Used
If multiple users need the same permissions, we attach policies to a Group once and add users to it.  
This is more efficient and prevents mistakes.

## Example Scenario
Company has 5 developers needing EC2 Start/Stop + S3 Read/Write:
- Create a Group: `developers`
- Attach EC2 and S3 policies to the group
- Add all five users to the group

Result: Simple, clean, scalable access control.
