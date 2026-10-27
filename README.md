# Cloud Labs Write-ups

Two write-ups from my cloud learning in June 2026: the TryHackMe Cloud Computing Fundamentals room and the flaws.cloud AWS security challenge.

I am a BSc (Hons) Computer System Engineering graduate from Nepal, working towards junior systems, network and cloud roles. I write up every lab I do so I understand it properly and so the next person does not have to start from zero. These are learning labs, not production work.

## What is in this repo

| File | What it covers |
|---|---|
| [01-cloud-computing-fundamentals-tryhackme.pdf](01-cloud-computing-fundamentals-tryhackme.pdf) | The TryHackMe Cloud Computing Fundamentals room: what EC2 is, how instance types work, picking a region, deploying virtual machines and reading the billing page. |
| [02-flaws-cloud-aws-walkthrough.pdf](02-flaws-cloud-aws-walkthrough.pdf) | All six levels of flaws.cloud, a challenge by Scott Piper about real AWS mistakes, written up level by level with the reason each one is dangerous and how to fix it. |

## 01. Cloud Computing Fundamentals (TryHackMe)

This room is not about hacking. It is about understanding the basics before touching cloud security.

- EC2 is a virtual computer in the cloud, and the instance type (like t3.micro or m5.large) decides how powerful and how expensive it is.
- Region matters. Closer to your users means lower latency, and sometimes data laws force a region on you.
- I deployed two machines, checked the billing page, stopped them and started them again. Only running machines cost credits, and a stopped machine costs nothing.
- My main takeaway: cloud billing is simple arithmetic, and that is why real teams use auto-stop and scheduled shutdowns.

## 02. flaws.cloud (AWS)

Each level is a different AWS mistake that really happens in production.

| Level | Mistake | What I learned |
|---|---|---|
| 1 | Public S3 bucket | Anyone can list and read a bucket with a public ACL. The fix is S3 Block Public Access. |
| 2 | "Any authenticated AWS user" access | This setting means anyone with any AWS account, not just your team. Name exact accounts or roles instead. |
| 3 | Keys left in git history | Deleting a file in a new commit does not remove it from history. Rotate any key that was ever committed. |
| 4 | Public EBS snapshot | A public snapshot exposes the whole disk, password files included. Keep snapshots private and encrypted. |
| 5 | SSRF to the EC2 metadata service | A server that fetches URLs can be tricked into reading its own IAM credentials from 169.254.169.254. IMDSv2 helps. |
| 6 | Over-permissive read access | Even a read-only auditor can map your whole account. Apply least privilege to everyone. |

## Tools and services I used

AWS CLI, S3, EC2, EBS, IAM, Lambda and API Gateway (flaws.cloud), Git, and the TryHackMe lab environment.

## A note on spoilers and safety

flaws.cloud and TryHackMe are training platforms. I wrote down how I reasoned and what I learned, and I did not use anything outside the intended challenge. Everything was done in the platforms' own environments.

## About me

- Portfolio: https://adbinmagar.netlify.app/
- Blog (The Grey Lens): https://thegreylens.hashnode.dev/
- LinkedIn: https://www.linkedin.com/in/adbin-magar
- Email: adbin8magar@gmail.com

I am currently studying for AZ-104 and learning Kubernetes and Terraform. If you spot a mistake in these write-ups, please tell me.
