# EKS

##Troubleshooting:
1) File association not found for extension .py
```aidl
assoc .py=py_auto_file
ftype py_auto_file="C:\Python38\python.exe" "%1" %*
```
***Note:** Change C:\Python38\python.exe to your python.exe path.*
2) Unauthorized or access denied (kubectl)
   
Help link: https://aws.amazon.com/ru/premiumsupport/knowledge-center/eks-api-server-unauthorized-error/

```aidl
You're not the cluster creator
If you didn't create the cluster, then complete the following steps:

1.    To see the configuration of your AWS CLI user or role, run the following command:

aws sts get-caller-identity

The output returns the ARN of the IAM user or role.

2.    Ask the cluster owner or admin to add your IAM user or role to aws-auth ConfigMap.

3.    To edit aws-auth ConfigMap in a text editor, the cluster owner or admin must run the following command:

kubectl edit configmap aws-auth -n kube-system

4.    To add an IAM user or IAM role, complete either of the following steps.

Add the IAM user to mapUsers. For example:

mapUsers: |
  - userarn: arn:aws:iam::XXXXXXXXXXXX:user/testuser
    username: testuser
    groups:
      - system:masters

Add the IAM role to mapRoles. For example:

mapRoles: |
  - rolearn: arn:aws:iam::XXXXXXXXXXXX:role/testrole
    username: testrole
    groups:
      - system:masters
```
## Create new kubectl .config
```aidl
aws eks \
  --region <region> update-kubeconfig \
  --name <cluster_name> \
  [--kubeconfig <config_name>]
```
Help link: https://en.sokube.ch/post/aws-kubernetes-aws-elastic-kubernetes-service-eks
