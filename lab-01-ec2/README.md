# Lab 01 — Launch Your First EC2 Instance

**Domain:** Cloud Technology  
**Difficulty:** Beginner  
**Time:** ~30 minutes  
**AWS Services:** EC2, Security Groups, Key Pairs

---

## Objective

Launch a Linux EC2 instance, understand its full lifecycle 
(pending → running → stopped → terminated), and learn the core 
compute concepts tested on the CCP exam.

---

## CCP Exam Concepts Covered

- EC2 = IaaS (Infrastructure as a Service)
- AMIs (Amazon Machine Images) — templates for launching instances
- Instance types (t2.micro = 1 vCPU, 1GB RAM)
- Security Groups = stateful firewalls
- Instance states: pending, running, stopped, terminated
- Shared Responsibility Model — AWS manages hardware, you manage the OS

---

## Step 1 — Create Your AWS Free Tier Account

1. Go to [aws.amazon.com](https://aws.amazon.com)
2. Click **Create a Free Account**
3. Follow the signup steps
4. Once inside, set your region to **us-east-1 (N. Virginia)**

> ⚠️ Before anything else — go to Billing > Billing Preferences 
> and enable billing alerts. Set an alarm at $5 so you're never 
> surprised by charges.

---

## Step 2 — Navigate to EC2

1. In the AWS Console search bar, type **EC2** and click it
2. You'll land on the EC2 Dashboard
3. This is where all your virtual machines live

> 📚 Exam tip: EC2 = IaaS. "Elastic" means you can scale up or 
> down on demand. Remember this.

---

## Step 3 — Launch an Instance

1. Click the orange **Launch Instance** button
2. Name it: `MyCCPLab01`
3. AMI: select **Amazon Linux 2023** (Free tier eligible)
4. Instance type: select **t2.micro** (Free tier eligible)

> 📚 Exam tip: t2.micro = 1 vCPU, 1GB RAM. Know that instance 
> families serve different purposes — compute, memory, storage optimized.

---

## Step 4 — Create a Key Pair

1. Under Key pair, click **Create new key pair**
2. Name it: `ccp-lab-key`
3. Type: **RSA**
4. Format: **.pem**
5. Click **Create key pair** — it downloads automatically
6. Save this file somewhere safe. You only get it once.

> 🔐 Key pairs are how you securely SSH into Linux instances. 
> AWS keeps the public key, you keep the private key.

---

## Step 5 — Configure Security Group

1. Under Network Settings, click **Edit**
2. Click **Create security group**
3. Name it: `ccp-lab-sg`
4. SSH (port 22) should already be listed
5. Change Source type to **My IP**

> 📚 Exam tip: Security Groups are STATEFUL — inbound traffic 
> allowed means the response is automatically allowed back out. 
> Network ACLs are STATELESS. Know the difference.

---

## Step 6 — Launch & Observe

1. Leave storage as default (8 GiB)
2. Click **Launch Instance**
3. Click **View all instances**
4. Watch the states change:
   - **Pending** → AWS is setting it up
   - **Running** → your instance is live
5. Note the Public IPv4 address in the details panel

> ✅ I just launched a virtual server in the cloud. That's EC2.

---

## Step 7 — Stop, Start, and Terminate

Select your instance and click **Instance state** to try each one:

| Action | What Happens | Billing |
|--------|-------------|---------|
| Stop | Shuts down, data preserved | No compute charge |
| Start | Boots back up | Compute resumes |
| Terminate | Permanently deleted | No more charges |

Go ahead and **Terminate** when done to avoid charges.

> 📚 Exam tip: Stopped ≠ Terminated. Stopped = paused, data saved. 
> Terminated = gone forever.

---

## What I Built

- Launched an Amazon Linux EC2 t2.micro instance
- Created an RSA key pair for secure access
- Configured a Security Group restricted to my IP
- Observed the full EC2 instance lifecycle
- Practiced stop, start, and terminate

---

## Key Takeaways

1. EC2 = IaaS — I manage the OS, AWS manages the hardware
2. AMIs are the templates used to launch instances
3. Security Groups are stateful firewalls
4. Stopped instances don't incur compute charges
5. Terminated instances are gone permanently — no undo

---
## NOTE 
✅ I have completed this lab and what my AZ instance ran was in (us-east-1b)


[Next → Lab 02 — Store Files with S3](../lab-02-s3/README.md)
