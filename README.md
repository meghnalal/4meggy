# Goldman Sachs DevOps/System Engineer Mock Interview (Marcus Digital Platform)

I want you to do well so this is on the harder end of the spectrum. Do not freak out if you do not know, just trying to prep you for the worst :). This Marcus thing makes them a fortune so reliability is number one, no messing about ;)

## IMPORTANT MEG!!

While technical skills are important, Goldman interviewers focus on future leadership potential. Emphasize accountability and initiative.

---

## ⏱️ Interview Structure

| Segment                    | Duration | Focus                                                                 |
|----------------------------|----------|------------------------------------------------------------------------|
| Technical Deep Dive     | 45 mins  | AWS, Terraform, CI/CD, Python, Docker, Monitoring, Security            |
| Behavioral Gauntlet     | 30 mins  | Ownership, failure, teamwork, learning mindset, stakeholder empathy    |
| Curveballs & Closing     | 15 mins  | Ethics, business awareness, lateral thinking, final sales pitch        |

---

## 🔧 Part 1: Technical Questions

1. You’ve inherited a Terraform project that uses hardcoded secrets and local state. What’s wrong and how do you fix it?

2. Build a multi-environment Terraform structure for dev/stage/prod.

3. Secure an S3 bucket so that it is only accessible through CloudFront.

4. Deploy a Lambda function securely and efficiently.

5. Build a GitLab CI pipeline for a Python microservice.

6. Explain the difference between blue/green and canary deployments. Which would you use and why?

7. What’s the difference between Docker bind mounts and volumes? When would you use each?

8. A Kubernetes pod is stuck in CrashLoopBackOff. Walk me through your debugging steps.

9. What would you monitor and alert on for a customer-facing service?

10. How would you reduce AWS costs in a dev/test environment?

---

## 🤝 Part 2: Behavioral Questions

11. Tell me about the worst outage you’ve ever caused. What happened and what did you learn?
### 🟥 Incident 

Worst outage I caused was when I approved an MR That had removed some testing logic. To give context this was a new feature FE implementation, it was a big MR that I allready reviewed a couple of time after some comments and follow up changes. On my last review I mainly focused on comments review changes without realising some component test were deleted. And when deleting test the pipeline will still pass because there is no failing test , and the code went to prod causing issues on other very important feature of the application.

### 🟧 Root Cause (RCA)  
- Because the MR was big it was easier to miss things 
- CI passed because the tests were gone, not because the code was safe.
- No Error boundary protection for production

### 🟩 Process Fix  
- First of all I decided that we should leverage more feature branches if there is a big change coming its easier to review bit by bit
- Implemented a checklist before and after anything went to production, we do extensive test to the feature itself but its also important to test everything especially with the main feature of application. So organised with the team to decide which features are tier A and they need a flow check no matter if the MR has nothing to do with that
- Most Important one to me its implementing error boundaries, if part of the component broke down the error propagates to top of the application , by implementing error boundaries that error stays contained at the lower component level without causing full app outages and it also triggered a metric in the BE so we could be notified 

### 🟦 Learning Takeaway 
Time invested in quality of the product its just as important as time invested in the developement, when you have big application its impossible to keep track of everything hence why leveraging error boundaries ci and metrics 

---

12. Describe a time you had to fix something critical under pressure.
### 🟥 Situation
So the situation was that there was a issue in the ingestion of the dataset that happens in the cloud.And this caused a very critical issue because that data gets used to sign off vehicles and also for testing across the whole company.

### 🟧 Action 
So the action that I took was immediatly focus on that task and trying track down where the issue is coming from.
I done that by force triggering ingestion and trying to analyse cloud logs to see if the problem is located in the triggering of the ingestion or the lower level code itself (image).
By doing that I found that the triggering worked but it wasnt running anything.
Because of that found out that the ingest image wasnt there anymore, we had coded in terraform to at least keep 5 copies of the ingention image but for some reason it wasnt there anymore.

### 🟩 Process Fix  
So to fix this i diverted in 2 solution:
1- Immediate outcome is to push image up so the ingestion back up and running
2- Long term solution was to find out why the image suddently got deleted and it turns out it was because the rule wasnt applied properly to the release pipeline and therefore why the image got deleted 

### 🟦 Learning Takeaway 

---
13. Describe a time you improved a DevOps process without being asked.

14. Describe a conflict with a developer. How did you resolve it?

15. What’s a recent DevOps tool you learned and why?

---

## 🧠 Part 3: Strategic Curveballs

16. You discover secrets committed to a public repo. What do you do?

17. Why is DevOps critical to the Marcus platform?

18. What DORA metrics do you care about and why?

19. If you were leading the Marcus platform team, what would you focus on in your first 90 days?