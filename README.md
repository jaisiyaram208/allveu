# Introduction 
This is the K2 autoscaling prototype based on EC2 and dynamic configuration by script execution at  start time via SSM automation
At this point is in minimal functional state and requires improvements
Wiki page: https://allvuesystems.atlassian.net/wiki/spaces/CE/pages/1701184025/K2+Autoscaling
Temporary domain name https://cs1.k2.ct.ws/ is pointed to public ALB CNAME

# Required improvements 
1.	Secrets managemement job to securely update customer secret with required sensitive values
      - potentially requires external secret outside of this template, solution is still in progress
2.	Amazon MQ vhost creation
3.	Review the code, remove hardcode and cleanup
4.	AWS CLI local install or replace with powershell native scripts
5.  Security review and hardening code for multitenant installation and isolation
6.  Variables
      - release version (artifacts)
7.  Improve SSM automation document to ensure the instance is not put in service is any step or secret failed (add exit codes logic into scripts)
8.  Enable autoscaling for CPU and Amazon MQ in autoscaling group
9. ALB healchecks for front and back
10. Split IaC core resources like ALB amazon MQ, Admin Secrets etc into separate pipeline
11. Create Customer secrets in separate job/pipeline (TBD)

#  Deployment related
EC2 dedicated runner is in build account (**7508) "K2-AutoScaling-Build-Acc" 
Secret "AppGoldenAMIadAdminSecret" must bu updated manually with correct values before scaling up  TBD

# Notes
Custom AMI ec2-builder logic is removed from the code if required can be reused form archive folder in this repo.