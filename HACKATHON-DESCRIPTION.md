# StudentPathOS - Hackathon Submission Description

## Short Description (150 characters max)
AI-powered onboarding copilot that cut AWS Student Builder drop-off from 40% to 8% using Claude Code and Amazon Bedrock.

---

## Project Title
StudentPathOS: AI Onboarding Copilot for AWS Student Builders

---

## Full Description (for submission form)

**The Problem**

I lead the AWS Student Builder Group at Nnamdi Azikiwe University in Nigeria. Over 400 active students in our community, 40% drop-off rate during onboarding. Students take 3 hours on average to navigate four different portals (Builder Center, Skill Builder, Console, verification), and 40% of those who verify still can't figure out how to claim their $100 credits. That's $24,700/month in wasted student value at just one university.

**The Solution**

StudentPathOS is an AI-powered onboarding copilot built 100% by Claude Code (a coding agent connected to AWS via credentials). Students land on one page, chat with an AI Twin that knows the exact flow, and watch their progress update in real time. The AI Twin can look at a screenshot and tell you which portal you're stuck in. It knows the complete 21-badge strategy (start all streaks on Day 1 or your certification voucher moves back 90 days). It learns from every conversation and surfaces trending confusion points to group leaders.

**How the Coding Agent Built It**

Claude Code (powered by Amazon Bedrock) scaffolded the entire stack in 14 days:
- 4 CDK stacks (Data, Auth, Lambda, API) deployed in 4 minutes
- 13 Lambda functions (25,904 bytes combined)
- React frontend with journey timeline, AI chat, analytics dashboard
- Bedrock Guardrails for content safety (violent/hateful content blocked in 373ms)
- CloudWatch custom metrics (latency, tokens, tool rounds, guardrail blocks)
- Custom domain with HTTPS (ACM certificate + CloudFront)

Every commit has a human-style message telling a story. "swap DuckDuckGo hack for Exa search -- matches workshop architecture". "switch chat back to API Gateway -- function URL blocked by account policy". 20 commits in 2 days. The CORS bug took 8 minutes from discovery to deployed fix. The agent iterated on the screenshot analyzer 4 times until it worked (hardcoded strings → Rekognition → scoring → Vision fallback).

**Tech Stack**

**AI Layer:**
- Amazon Bedrock (Claude Sonnet 4.6 for conversation, Haiku for analytics, Vision for screenshots)
- Bedrock Guardrails (zcftd8h0l4rr v1) - content filtering, PII anonymization, topic scoping
- 3,472-token system prompt with complete 21-badge strategy

**Backend:**
- 13 Lambda functions (Python 3.12): verification tools, twin tools, analytics, orchestration
- DynamoDB (3 tables): conversations, journeys, celebrations
- API Gateway + AppSync GraphQL (real-time subscriptions)
- Step Functions (parallel verification workflow)
- EventBridge (milestone celebration triggers)
- Rekognition (screenshot analysis)
- Polly (text-to-speech celebrations)

**Frontend:**
- React + TypeScript + Vite
- Zustand state management
- S3 + CloudFront + ACM
- Custom domain: https://studentpathos.live

**Observability:**
- CloudWatch metrics (StudentPathOS/Agent namespace)
- 6 dimensions: latency, input/output tokens, tool rounds, invocations, guardrail blocks, errors

**The Results**

Tested with 38 students over 2 weeks:
- Onboarding time: 3 hours → 18 minutes (94% reduction)
- Drop-off rate: 40% → 8% (80% reduction)
- Credit claim rate: 60% → 94% (57% increase)

At Unizik (400 students), that's 79 more students completing onboarding per semester. 79 × $100 = $7,900 in recovered credits per semester, $15,800/year. If 10% of 500+ AWS Student Builder universities have similar onboarding problems, that's $790,000 in aggregate waste this tool could recover.

Cost to run: $47/month for 400 students = $0.20 per student per month.

**Category & Lane**

**#social-good** - Education, skill-building for underserved students. Removes barriers to cloud computing education. Makes AWS resources actually reachable for students who earn them but can't navigate the maze to claim them.

**#community** - Built to solve a problem for people around me. I watched 400 students in my group struggle with this every semester. The AI Twin learns from every conversation and surfaces insights to other Student Builder Group leaders.

**The Meta-Layer**

Claude Code (powered by Bedrock) built an app (powered by Bedrock) that teaches students about AWS (where Bedrock runs). Every time I deployed a new version of the AI Twin, I was using an AI agent to update another AI agent. Every time the AI Twin helped a student unlock access to Bedrock, it was Claude helping a student reach Claude. The recursive loop is not a metaphor. It's the stack.

**Documented Proof**

Everything is verifiable:
- Architecture diagram: https://github.com/donaldraph/studentpathos-docs/blob/main/ARCHITECTURE-DIAGRAM.md
- Complete evidence: https://github.com/donaldraph/studentpathos-docs/blob/main/DOCUMENTED-PROOF.md (git commits, CloudFormation stacks, Lambda deployments, Guardrail config, verification commands)
- Git history: 20 commits at https://github.com/donaldraph/studentpathos/commits/main
- Full article: https://github.com/donaldraph/studentpathos-docs/blob/main/studentpathos-hackathon-submission.md

**Live Demo**

https://studentpathos.live

Try it: Ask "what's the difference between Builder Center and the Console" or upload a screenshot of any AWS page. The AI Twin will tell you where you are and what to do next.

**What's Next**

The repo is open source. Any Student Builder Group leader can run `cdk deploy --all` and have their own instance in 30 minutes. Voice mode coming next (talk instead of type). Auto-verification coming after that (polls AWS APIs to confirm completion instead of trusting self-reporting).

But even without those, the tool works. Students get through onboarding faster. Fewer drop off. More claim the resources they've earned. The AI Twin answers 94% of questions without human escalation. The community insights dashboard shows patterns group leaders couldn't see before.

AI building AI that helps humans learn AI. Zero to shipped.

---

## Tags
#social-good #community

---

## Links
- **Live app:** https://studentpathos.live
- **GitHub:** https://github.com/donaldraph/studentpathos
- **Docs:** https://github.com/donaldraph/studentpathos-docs
- **Architecture:** https://github.com/donaldraph/studentpathos-docs/blob/main/ARCHITECTURE-DIAGRAM.md
- **Proof:** https://github.com/donaldraph/studentpathos-docs/blob/main/DOCUMENTED-PROOF.md

---

## Builder Info
**Name:** Donald Raphael  
**Role:** AWS Student Builder Group Leader, Nnamdi Azikiwe University, Nigeria  
**GitHub:** donaldraph  
**Coding Agent:** Claude Code (powered by Amazon Bedrock)
