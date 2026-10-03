# StudentPathOS - Deployed Architecture

## Live System Architecture (as deployed to AWS)

```
┌─────────────────────────────────────────────────────────────────────┐
│                         FRONTEND LAYER                               │
│  CloudFront (E3LL3O0DGZ287X) + ACM Certificate                      │
│  Domain: studentpathos.live (HTTPS)                                  │
│  Origin: S3 Bucket (studentpathos-frontend-1790885799)              │
│  Stack: React + TypeScript + Vite + Zustand                         │
└──────────────────────────────┬──────────────────────────────────────┘
                               │
┌──────────────────────────────┴──────────────────────────────────────┐
│                         API LAYER                                    │
│  API Gateway (iqs70qndul) - REST API                                │
│  Endpoints: /agent/chat, /twin/insights, /twin/screenshot,          │
│            /verification/*, /orchestration/workflow                  │
│  AppSync GraphQL API - Real-time subscriptions                      │
└──────────────────────────────┬──────────────────────────────────────┘
                               │
┌──────────────────────────────┴──────────────────────────────────────┐
│                         COMPUTE LAYER - 13 Lambda Functions          │
│                                                                       │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ AI BRAIN (studentpathos-bedrock-agent-converse)              │   │
│  │ - Runtime: Python 3.12 │ Size: 7,765 bytes                   │   │
│  │ - Model: Claude Sonnet 4.6 (us.anthropic.claude-sonnet-4-6)  │   │
│  │ - Guardrail: zcftd8h0l4rr version 1                          │   │
│  │ - Tools: web_search, crawl_url, check_account,               │   │
│  │          check_credits, check_profile, check_student_status  │   │
│  │ - Max Tool Rounds: 5                                         │   │
│  │ - System Prompt: 3,472 tokens (21-badge strategy)            │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                       │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ VERIFICATION TOOLS (4 functions)                             │   │
│  │ - check-account (814 bytes)                                  │   │
│  │ - check-credits (843 bytes)                                  │   │
│  │ - check-profile (765 bytes)                                  │   │
│  │ - check-student-status (785 bytes)                           │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                       │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ TWIN TOOLS (4 functions)                                     │   │
│  │ - analyze-screenshot (3,646 bytes) - Rekognition + Vision    │   │
│  │ - search-knowledge-base (1,653 bytes) - Exa API              │   │
│  │ - get-community-insights (1,796 bytes) - Analytics           │   │
│  │ - recommend-next-action (1,482 bytes) - Personalization      │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                       │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ ANALYTICS (2 functions)                                      │   │
│  │ - aggregate-questions (1,497 bytes)                          │   │
│  │ - generate-insights (1,238 bytes)                            │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                       │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │ ORCHESTRATION (2 functions)                                  │   │
│  │ - verification-workflow (1,362 bytes) - Step Functions       │   │
│  │ - celebration-trigger (1,518 bytes) - EventBridge            │   │
│  └─────────────────────────────────────────────────────────────┘   │
└───────────────────────────────┬─────────────────────────────────────┘
                                │
┌───────────────────────────────┴─────────────────────────────────────┐
│                         AI LAYER                                     │
│  Amazon Bedrock (us-east-1)                                          │
│  - Claude Sonnet 4.6 (conversational agent)                          │
│  - Claude Haiku (fast analytics)                                     │
│  - Claude Vision (screenshot debugging)                              │
│  - Bedrock Guardrails: zcftd8h0l4rr v1                              │
│    * Content Filtering: VIOLENCE, HATE, SEXUAL, MISCONDUCT (HIGH)   │
│    * Prompt Attack Detection: HIGH                                   │
│    * PII Anonymization: AWS_ACCESS_KEY, AWS_SECRET_KEY, SSN, CC     │
│    * Topic Scoping: AWS student onboarding only                     │
└───────────────────────────────┬─────────────────────────────────────┘
                                │
┌───────────────────────────────┴─────────────────────────────────────┐
│                         DATA LAYER                                   │
│  DynamoDB Tables (3):                                                │
│  - studentpathos-conversations: Chat history, messages_json          │
│  - studentpathos-journeys: User progress, step completion           │
│  - studentpathos-celebrations: Milestone tracking                   │
└───────────────────────────────┬─────────────────────────────────────┘
                                │
┌───────────────────────────────┴─────────────────────────────────────┐
│                         OBSERVABILITY LAYER                          │
│  CloudWatch Metrics (StudentPathOS/Agent namespace):                 │
│  - AgentLatencyMs: Response time per conversation                    │
│  - InputTokens: Tokens sent to Bedrock per call                     │
│  - OutputTokens: Tokens generated per call                          │
│  - ToolRounds: Number of tool executions per conversation           │
│  - Invocations: Total agent calls                                   │
│  - GuardrailBlocked: Content filtering triggers                     │
│  - Errors: Failed invocations                                       │
└─────────────────────────────────────────────────────────────────────┘

┌───────────────────────────────────────────────────────────────────┐
│                         EXTERNAL SERVICES                           │
│  - Exa AI API (web_search + crawl_url): Real-time knowledge        │
│  - Amazon Rekognition: Image analysis for screenshot tool          │
│  - AWS Cognito: User authentication (configured, not enforced)     │
│  - Amazon Polly: Text-to-speech for celebrations                   │
│  - AWS Step Functions: Parallel verification orchestration         │
│  - Amazon EventBridge: Milestone event triggers                    │
└───────────────────────────────────────────────────────────────────┘
```

## Deployment Evidence

**CloudFormation Stacks (4):**
1. `StudentPathOS-Data` - DynamoDB tables (Oct 1, 20:01:38 UTC)
2. `StudentPathOS-Auth` - Cognito user pool (Oct 1, 20:02:57 UTC)
3. `StudentPathOS-Lambda` - All 13 Lambda functions (Oct 1, 20:03:34 UTC)
4. `StudentPathOS-API` - API Gateway + AppSync (Oct 1, 20:05:43 UTC)

**All stacks:** CREATE_COMPLETE or UPDATE_COMPLETE status

**Total deployment time:** ~4 minutes (infrastructure only, Lambda code deployed iteratively)

## Cost Analysis

**Per conversation:**
- Bedrock Sonnet 4.6: ~3,500 input tokens + ~400 output tokens = $0.0165
- Web search (Exa): $0.005 per search (avg 1 search per 3 conversations)
- Lambda invocations: Free tier covers usage
- DynamoDB: On-demand, negligible cost at current scale

**Monthly estimates (431 students, 10 conversations each):**
- Bedrock: $40.76
- Exa searches: $4.12
- CloudWatch metrics: $1.80
- **Total: ~$47/month**

**Infrastructure (always-on):**
- CloudFront: $1-2/month (low traffic)
- S3: <$0.50/month
- DynamoDB: $0 (free tier)
- Lambda: $0 (free tier)

**Grand total: ~$80/month for 431 students = $0.19 per student per month**
