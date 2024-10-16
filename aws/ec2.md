# EC2
## Minimal Network Config for SSH
[via StackOverflow](https://stackoverflow.com/a/56386800)

To be able to SSH into an Amazon EC2 instance, you'll need the following:

-   An **Amazon VPC** (the default one is fine, or create your own)
-   An **Internet Gateway** attached to the VPC (to connect it to the Internet)
-   A **public subnet**, which is defined as a subnet that has a route table where the route table sends traffic destined for `0.0.0.0/0` to the Internet Gateway
-   An **Amazon EC2 instance** in the public subnet, presumably a Linux instance since you want to SSH to it
-   When launching the instance, nominate a **Keypair**. If you launch from an Amazon-provided AMI (eg Amazon Linux 2), the keypair will be copied to `/users/ec2-user/.ssh/authorized_keys` at startup.
-   The instance should either be launched with **Auto-assign Public IP** to receive a random public IP address, or associate the instance with an **Elastic IP address** to associate a static IP address
-   A **security group** attached to the EC2 instance permitting inbound SSH access (port 22) either from `0.0.0.0/0` or your own IP address
-   Don't play with the **Network Access Control List (NACL)** settings - they default to allowing all traffic in/out

To connect to the instance:

```
ssh -i YOUR-KEYPAIR.pem ec2-user@IP-ADDRESS
```

If the connection is **immediately** rejected, it suggests a problem with the keypair.

If the connection **takes some time** before failing, it suggests a network-related problem because it is unable to contact the instance. Some corporate networks **block outbound SSH access**, so try again from a different network (home vs office, or even tethered via your phone) to try and identify the issue.