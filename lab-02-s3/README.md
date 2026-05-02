# Lab 02 — S3 Storage

**Domain:** Cloud Storage
**Difficulty:** Beginner
**Time:** ~25 minutes
**AWS Services:** Amazon S3, Bucket Policies

---

## What I Did

Created a real S3 bucket, threw some files in it, looked at storage 
classes, and ended up hosting an actual website out of it. 
No servers. Nothing. Just S3.

---

## What the CCP Exam Wants Me to Know

- S3 stores objects — not the same as a hard drive (that's EBS)
- Bucket names have to be unique across all of AWS, not just your account
- S3 is built to never lose your data — 99.999999999% durability (11 nines)
- Different storage classes exist depending on how often you need your files
- You can host a static website straight from a bucket

---

## Step 1 — Get to S3

1. I searched **S3** in the console and I clicked it
2. I notice there's no region dropdown at the top — S3 is global
3. I Click **Create bucket**

> 📚 Exam tip: S3 is global but my bucket lives in a specific region
> No two buckets in all of AWS can have the same name.

---

## Step 2 — Create the Bucket

1. I name my bucket something unique like `rod-ccp-lab-2026`
2. Region: **us-east-1**
3. Leave everything else as default
4. Click **Create bucket**

> ⚠️ If the name is taken I just throw some numbers at the end of it.

---

## Step 3 — Upload Some Files

1. I clicked into my bucket
2. I Clicked **Upload > Add files**
3. I Grabbed any image or text file off my computer
4. Click **Upload**

> 📚 Exam tip: Files in S3 are called OBJECTS. 
> The bucket is just the container that holds them.

---

## Step 4 — Check Out Storage Classes

1. I clicked the filea I just uploaded
2. Go to the **Properties** tab
3. Look at **Storage class** — it says S3 Standard

Here's what the different classes mean:

| Storage Class | Best For | How Fast |
|---------------|----------|----------|
| S3 Standard | Files you use all the time | Instant |
| S3 Standard-IA | Files you rarely touch | Instant |
| S3 Glacier Instant | Archives you might need fast | Instant |
| S3 Glacier Flexible | Archives you can wait on | Minutes to hours |
| S3 Glacier Deep Archive | Long term storage, rarely needed | Up to 12 hours |

> 📚 Exam tip: The cheaper the storage class the slower you get 
> your files back. Glacier = cheapest, slowest.

---

## Step 5 — Build a Simple HTML File

On my computer I opened TextEdit and paste this:

```html
<!DOCTYPE html>
<html>
<head><title>My AWS S3 Site</title></head>
<body>
  <h1>Hello from Amazon S3!</h1>
  <p>No servers. Just S3.</p>
</body>
</html>
```

Saved it as `index.html` then I uploaded to my bucket the same way as Step 3.

---

## Step 6 — Turn on Static Website Hosting

1. I Clicked on my bucket
2. I went to **Properties** tab
3. I scrolled all the way down to **Static website hosting**
4. Clicked **Edit** and select **Enable**
5. Under **Index document** type `index.html`
6. I clicked **Save changes**
7. I Copied the website URL at the bottom

---

## Step 7 — Make It Public

By default S3 blocks everything. Here's how I open it up:

1. I went to **Permissions** tab
2. Click **Edit** under **Block public access**
3. Uncheck **Block all public access**
4. I typed `confirm` and save

5. I scrolled to **Bucket policy** and click **Edit**
6. I Paste this and swap in my actual bucket name:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::YOUR-BUCKET-NAME/*"
    }
  ]
}
```

7. I saved it and visited the website URL http://rod-ccp-lab-2026.s3-website-us-east-1.amazonaws.com/

> ✅ Completed. That's a live website running out of S3. No servers, 
> no maintenance, just a bucket.

---

## What I Walked Away With

- S3 stores objects not files like a hard drive
- Bucket names are globally unique — treat them like domain names
- Storage classes let you save money based on how often you need stuff
- Bucket policies are how you control who sees what
- You can host a whole website from S3 with zero servers

---

[← Lab 01 — EC2](../lab-01-ec2/README.md) | [→ Lab 03 — IAM](../lab-03-iam/README.md)
