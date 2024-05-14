Prerequisites:
Terraform 
AWS CLI and 
KUBECTL 

# EKS Setup with Terraform

Prerequisites:
```
Terraform 
AWS CLI and 
KUBECTL 
```

# The script installs terraform, awscli and kubectl on ubuntu.
Provide the executable permission to script.sh file, and run it if you are on Ubuntu or you have wsl installed on windows.

```
sudo chmod +x script.sh
./script.sh
```
This script will install Terraform, AWS cli, Kubectl.

Check versions

```
aws --version
kubectl version --client
terraform --version
```
Run Terraform init

NOTE: Don’t forgot to change the s3 bucket name in the backend.tf file. For testing purposes you cantake out the backend.tf to store statefiles locally(not advisable anyway)


```
terraform init
```
Now run terraform validate and terraform plan

```
terraform validate
terraform plan
```
Now Run terraform apply to provision cluster.

```
terraform apply --auto-approve
```
Update the Kubernetes configuration

Make sure to change your desired region
Note: If you change the cluster name in the main.tf, remember to make the change in this command from "--name EKS_CLOUD" to your preferred "--name <preferred clustername>"

```
aws eks update-kubeconfig --name EKS_CLOUD --region us-east-2
```

# Take down cluster
When done with your infrastructure, run terraform destroy to take it down.
```
terraform destroy --auto-approve
```
