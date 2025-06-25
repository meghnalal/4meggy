## Technical Expectations

**Q1:** Identify security risks (hardcoded secrets), explain why local state is bad. Fix using S3 + DynamoDB backend, secrets manager, IaC linting/policy.

**Q2:** Use Terraform modules, workspaces or separate backends, per-env vars, outputs. Tagging, IAM boundaries.

**Q3:** Block public access on S3. Use OAI/OAC in CloudFront, restrict bucket policy to allow only CloudFront.

**Q4:** Deploy with IAM least privilege, secrets manager, versioning. Monitor via CloudWatch. Use Terraform/SAM.

**Q5:** GitLab CI: Lint → Test → Build → Deploy → Approve. Use secrets mgmt, rollback, env isolation.

**Q6:** Blue/green = switch all traffic. Canary = % routing. Marcus = Canary preferred (lower risk, progressive delivery).

**Q7:** Volumes = managed storage, persist between container restarts. Bind = host path, dev only.

**Q8:** Use `kubectl describe/logs`. Check liveness/readiness probes, image pulls, secrets/env, crash loops.

**Q9:** Metrics: CPU, memory, latency, 5xx. Logs: aggregated and indexed. Tools: ELK, CloudWatch, Prometheus. Alert on anomalies.

**Q10:** Spot instances, auto-shutdown, orphaned resources, S3 lifecycle rules, use of budget alerts.

---

## Behavioral Expectations

**Q11:** Full ownership, no excuses. Clear RCA and process fix. Learning takeaway.

**Q12:** Calm under fire, methodical troubleshooting, team communication, postmortem awareness.

**Q13:** Show proactive initiative. Automation, time saved, quality improved. Ideally measurable impact.

**Q14:** Diplomatic conflict handling. Explain reasoning. Used data. Aligned on outcome.

**Q15:** Show curiosity and practical learning. Self-taught tool used at work or in lab. Bonus if applied in real use.

---

## Strategic Curveballs

**Q16:** Revoke keys, rotate creds, git filter-history, add pre-commit scanners. Raise internal alert.

**Q17:** DevOps = trust, speed, compliance. Marcus = customer-facing. Reliability is non-negotiable.

**Q18:** DORA: Deployment freq, lead time, MTTR, change fail rate. Goal: improve velocity without risk.

**Q19:** Day 1 focus: infra audit, fix IaC, improve CI/CD, tag resources, implement budgets, observability.

---

## Goldman Internal Scoring Card

| Trait         | Weak           | Average        | Strong                          |
|---------------|----------------|----------------|----------------------------------|
| Technical     | Vague answers  | Surface-level  | Deep, tool-aware, structured     |
| Ownership     | Blames others  | Neutral        | Clear responsibility, fix-minded |
| Communication | Rambling       | Decent         | Structured, concise, confident   |
| Strategic     | Tactical only  | Some vision    | Big-picture, platform thinking   |