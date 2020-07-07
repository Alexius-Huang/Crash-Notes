---
description: Instance of AWS Serve
---

# AWS EC2

## Creating SSH Keys

Enter the "Network and Security" section, then enter the "Key Pairs" part.

Create an SSH keypair, option "pem" for Linux or MacOS.

## Entering Instance

After the instance is created, copy the public IP address.

 Use the SSH client:

```text
ssh -i <ec2-key-name>.pem ec2-user@<ip-address>
```

