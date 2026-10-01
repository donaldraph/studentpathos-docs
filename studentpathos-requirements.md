# StudentPathOS - Complete Requirements & Tools

## 📋 PREREQUISITES CHECKLIST

### Required Accounts:
- [ ] AWS Account (with admin access)
- [ ] AWS Educate / Student Builder account
- [ ] GitHub account (for version control)
- [ ] Figma account (for design - free tier OK)
- [ ] Node.js installed (v20.x LTS)
- [ ] Python installed (3.12.x)

---

## 🛠️ DEVELOPMENT ENVIRONMENT

### System Requirements:
```bash
OS: Linux (Ubuntu/Debian) / macOS / Windows (WSL2)
RAM: Minimum 8GB, Recommended 16GB
Disk: 10GB free space
CPU: Multi-core processor (development build performance)
```

### Required CLI Tools:
```bash
# Node.js & npm
node --version    # Should be v20.x
npm --version     # Should be 10.x+

# AWS CLI
aws --version     # Should be aws-cli/2.x

# AWS CDK
cdk --version     # Should be 2.x

# Git
git --version     # Any recent version

# Python
python3 --version # Should be 3.12.x
pip3 --version    # Latest

# Optional but recommended
jq --version      # JSON processing
curl --version    # API testing
```

---

## 📦 NPM PACKAGES (Frontend)

### package.json for React Frontend:
```json
{
  "name": "studentpathos-frontend",
  "version": "1.0.0",
  "type": "module",
  "scripts": {
    "dev": "vite",
    "build": "tsc && vite build",
    "preview": "vite preview",
    "lint": "eslint . --ext ts,tsx --report-unused-disable-directives --max-warnings 0",
    "format": "prettier --write \"src/**/*.{ts,tsx,css,md}\""
  },
  "dependencies": {
    "react": "^18.3.1",
    "react-dom": "^18.3.1",
    "react-router-dom": "^6.22.0",
    
    "@aws-amplify/ui-react": "^6.1.0",
    "aws-amplify": "^6.0.0",
    
    "zustand": "^4.5.0",
    "react-hook-form": "^7.50.0",
    "zod": "^3.22.4",
    "@hookform/resolvers": "^3.3.4",
    
    "@radix-ui/react-dialog": "^1.0.5",
    "@radix-ui/react-dropdown-menu": "^2.0.6",
    "@radix-ui/react-tabs": "^1.0.4",
    "@radix-ui/react-toast": "^1.1.5",
    "@radix-ui/react-tooltip": "^1.0.7",
    "@radix-ui/react-progress": "^1.0.3",
    "@radix-ui/react-avatar": "^1.0.4",
    
    "class-variance-authority": "^0.7.0",
    "clsx": "^2.1.0",
    "tailwind-merge": "^2.2.1",
    "tailwindcss-animate": "^1.0.7",
    
    "framer-motion": "^11.0.5",
    "lottie-react": "^2.4.0",
    
    "lucide-react": "^0.344.0",
    
    "recharts": "^2.12.0",
    
    "date-fns": "^3.3.1",
    
    "react-markdown": "^9.0.1",
    "remark-gfm": "^4.0.0",
    
    "sonner": "^1.4.0",
    
    "@tanstack/react-query": "^5.25.0",
    
    "axios": "^1.6.7"
  },
  "devDependencies": {
    "@types/react": "^18.2.56",
    "@types/react-dom": "^18.2.19",
    "@typescript-eslint/eslint-plugin": "^7.0.2",
    "@typescript-eslint/parser": "^7.0.2",
    "@vitejs/plugin-react-swc": "^3.5.0",
    "autoprefixer": "^10.4.18",
    "eslint": "^8.56.0",
    "eslint-plugin-react-hooks": "^4.6.0",
    "eslint-plugin-react-refresh": "^0.4.5",
    "postcss": "^8.4.35",
    "prettier": "^3.2.5",
    "prettier-plugin-tailwindcss": "^0.5.11",
    "tailwindcss": "^3.4.1",
    "typescript": "^5.3.3",
    "vite": "^5.1.4",
    "vite-plugin-svgr": "^4.2.0",
    "vitest": "^1.3.1",
    "@vitest/ui": "^1.3.1"
  }
}
```

---

## 📦 NPM PACKAGES (Backend - CDK)

### package.json for AWS CDK Infrastructure:
```json
{
  "name": "studentpathos-infrastructure",
  "version": "1.0.0",
  "scripts": {
    "build": "tsc",
    "watch": "tsc -w",
    "cdk": "cdk",
    "deploy": "cdk deploy --all",
    "destroy": "cdk destroy --all",
    "synth": "cdk synth",
    "diff": "cdk diff"
  },
  "devDependencies": {
    "@types/node": "^20.11.20",
    "aws-cdk": "^2.132.0",
    "ts-node": "^10.9.2",
    "typescript": "~5.3.3"
  },
  "dependencies": {
    "aws-cdk-lib": "^2.132.0",
    "constructs": "^10.3.0",
    
    "@aws-cdk/aws-lambda-python-alpha": "^2.132.0-alpha.0",
    
    "dotenv": "^16.4.5"
  }
}
```

---

## 🐍 PYTHON PACKAGES (Lambda Functions)

### requirements.txt for Lambda Layers:
```txt
# AWS SDK
boto3==1.34.52
botocore==1.34.52

# Bedrock
anthropic==0.18.1

# Image Processing (for screenshot analysis)
Pillow==10.2.0
opencv-python-headless==4.9.0.80

# Data Processing
pydantic==2.6.3
pydantic-settings==2.2.1

# HTTP
requests==2.31.0
httpx==0.27.0

# Utilities
python-dateutil==2.8.2
pytz==2024.1

# Testing (dev only)
pytest==8.0.2
moto==5.0.2
```

---

## 🎨 DESIGN & UI TOOLS

### Required Design Tools:
```bash
# Figma (Web-based)
URL: https://figma.com
Purpose: UI mockups, component design, prototyping
Plan: Free tier sufficient

# Excalidraw (Web-based)
URL: https://excalidraw.com
Purpose: Diagram sketching, architecture diagrams, annotations
Plan: Free, no account needed

# LottieFiles (Web-based)
URL: https://lottiefiles.com
Purpose: Celebration animations (confetti, milestones)
Plan: Free tier (download animations)

# Lucide Icons
URL: https://lucide.dev
Purpose: Icon library (already in React package)
Included in: lucide-react npm package

# AWS Architecture Icons
URL: https://aws.amazon.com/architecture/icons/
Purpose: AWS service icons for diagrams
Download: Free official icon set

# Coolors
URL: https://coolors.co
Purpose: Color palette generation & testing
Plan: Free
```

### Browser Extensions (Optional but Helpful):
```
- React Developer Tools (Chrome/Firefox)
- AWS Toolkit for Chrome
- Axe DevTools (Accessibility testing)
- JSON Formatter
- ColorZilla (Color picker)
```

---

## 🔧 AWS SERVICES CONFIGURATION

### Required AWS Services (Enable in Console):
```
✓ Amazon Bedrock (us-east-1 recommended)
  - Request model access:
    ✓ Claude 3.5 Sonnet
    ✓ Claude 3.5 Haiku
    ✓ Claude 3 Opus (optional)
    ✓ Titan Embeddings G1
    ✓ Nova Micro (if available)

✓ AWS Amplify (for hosting)
✓ Amazon API Gateway
✓ AWS Lambda
✓ Amazon DynamoDB
✓ Amazon S3
✓ Amazon CloudFront
✓ AWS Step Functions
✓ Amazon EventBridge
✓ AWS AppSync (GraphQL)
✓ Amazon Cognito
✓ Amazon Polly (Neural voices)
✓ Amazon CloudWatch
✓ AWS X-Ray (for tracing)
✓ Amazon QuickSight (optional, for analytics dashboard)
✓ AWS Secrets Manager
✓ AWS IAM (for roles & policies)
✓ AWS Certificate Manager (for custom domain)
```

### AWS CLI Configuration:
```bash
# Configure AWS credentials
aws configure

# Verify credentials
aws sts get-caller-identity

# Bootstrap CDK (one-time per account/region)
cdk bootstrap aws://ACCOUNT-ID/us-east-1

# Check Bedrock model access
aws bedrock list-foundation-models --region us-east-1 --query "modelSummaries[?contains(modelId,'claude')].modelId"
```

---

## 📁 PROJECT STRUCTURE

```
studentpathos/
├── README.md
├── .gitignore
├── package.json
│
├── frontend/                          # React application
│   ├── package.json
│   ├── vite.config.ts
│   ├── tsconfig.json
│   ├── tailwind.config.js
│   ├── postcss.config.js
│   ├── index.html
│   │
│   ├── public/
│   │   ├── favicon.ico
│   │   ├── portal-screenshots/
│   │   └── celebration-assets/
│   │
│   └── src/
│       ├── main.tsx                   # Entry point
│       ├── App.tsx                    # Root component
│       ├── index.css                  # Global styles
│       │
│       ├── components/
│       │   ├── ui/                    # Shadcn/ui components
│       │   │   ├── button.tsx
│       │   │   ├── dialog.tsx
│       │   │   ├── toast.tsx
│       │   │   └── ...
│       │   │
│       │   ├── layout/
│       │   │   ├── Header.tsx
│       │   │   ├── Sidebar.tsx
│       │   │   └── Footer.tsx
│       │   │
│       │   ├── journey/
│       │   │   ├── JourneyTimeline.tsx
│       │   │   ├── ProgressBar.tsx
│       │   │   ├── MilestoneCard.tsx
│       │   │   └── NextActionButton.tsx
│       │   │
│       │   ├── twin/
│       │   │   ├── ChatInterface.tsx
│       │   │   ├── TwinAvatar.tsx
│       │   │   ├── MessageBubble.tsx
│       │   │   └── VoiceToggle.tsx
│       │   │
│       │   ├── portal/
│       │   │   ├── PortalComparison.tsx
│       │   │   ├── AnnotatedScreenshot.tsx
│       │   │   └── InteractiveTour.tsx
│       │   │
│       │   ├── verification/
│       │   │   ├── AccountConnector.tsx
│       │   │   ├── StatusChecker.tsx
│       │   │   └── VerificationWizard.tsx
│       │   │
│       │   ├── analytics/
│       │   │   ├── CommunityInsights.tsx
│       │   │   ├── MetricsDashboard.tsx
│       │   │   └── ProgressChart.tsx
│       │   │
│       │   └── celebration/
│       │       ├── ConfettiAnimation.tsx
│       │       ├── MilestoneModal.tsx
│       │       └── CelebrationSound.tsx
│       │
│       ├── pages/
│       │   ├── Home.tsx
│       │   ├── Dashboard.tsx
│       │   ├── Portal Comparison.tsx
│       │   ├── Community.tsx
│       │   └── Settings.tsx
│       │
│       ├── hooks/
│       │   ├── useTwin.ts
│       │   ├── useJourneyState.ts
│       │   ├── useVerification.ts
│       │   └── useCommunityData.ts
│       │
│       ├── stores/
│       │   ├── journeyStore.ts         # Zustand store
│       │   ├── twinStore.ts
│       │   └── settingsStore.ts
│       │
│       ├── services/
│       │   ├── api.ts                  # API client
│       │   ├── amplify.ts              # Amplify config
│       │   ├── bedrock.ts              # Bedrock API
│       │   └── websocket.ts            # AppSync subscriptions
│       │
│       ├── types/
│       │   ├── journey.ts
│       │   ├── twin.ts
│       │   ├── verification.ts
│       │   └── community.ts
│       │
│       └── utils/
│           ├── formatters.ts
│           ├── validators.ts
│           └── constants.ts
│
├── infrastructure/                     # AWS CDK
│   ├── package.json
│   ├── cdk.json
│   ├── tsconfig.json
│   │
│   ├── bin/
│   │   └── app.ts                     # CDK app entry
│   │
│   └── lib/
│       ├── networking-stack.ts        # VPC, CloudFront
│       ├── auth-stack.ts              # Cognito
│       ├── data-stack.ts              # DynamoDB, S3
│       ├── compute-stack.ts           # Lambda functions
│       ├── api-stack.ts               # API Gateway, AppSync
│       ├── orchestration-stack.ts     # Step Functions, EventBridge
│       ├── ai-stack.ts                # Bedrock Agents, Knowledge Bases
│       ├── monitoring-stack.ts        # CloudWatch, X-Ray
│       └── frontend-stack.ts          # Amplify hosting
│
├── lambda/                            # Lambda function code
│   ├── shared/                        # Shared utilities
│   │   ├── __init__.py
│   │   ├── aws_clients.py
│   │   ├── models.py
│   │   └── utils.py
│   │
│   ├── verification-tools/
│   │   ├── check-account/
│   │   │   ├── handler.py
│   │   │   └── requirements.txt
│   │   │
│   │   ├── check-profile/
│   │   │   ├── handler.py
│   │   │   └── requirements.txt
│   │   │
│   │   ├── check-credits/
│   │   │   ├── handler.py
│   │   │   └── requirements.txt
│   │   │
│   │   └── check-student-status/
│   │       ├── handler.py
│   │       └── requirements.txt
│   │
│   ├── twin-tools/
│   │   ├── analyze-screenshot/
│   │   │   ├── handler.py
│   │   │   └── requirements.txt
│   │   │
│   │   ├── search-knowledge-base/
│   │   │   ├── handler.py
│   │   │   └── requirements.txt
│   │   │
│   │   ├── get-community-insights/
│   │   │   ├── handler.py
│   │   │   └── requirements.txt
│   │   │
│   │   └── recommend-next-action/
│   │       ├── handler.py
│   │       └── requirements.txt
│   │
│   ├── orchestration/
│   │   ├── verification-workflow/
│   │   │   ├── handler.py
│   │   │   └── requirements.txt
│   │   │
│   │   └── celebration-trigger/
│   │       ├── handler.py
│   │       └── requirements.txt
│   │
│   └── analytics/
│       ├── aggregate-questions/
│       │   ├── handler.py
│       │   └── requirements.txt
│       │
│       └── generate-insights/
│           ├── handler.py
│           └── requirements.txt
│
├── docs/                              # Documentation
│   ├── ARCHITECTURE.md
│   ├── API.md
│   ├── DEPLOYMENT.md
│   ├── DEMO_SCRIPT.md
│   └── AGENT_PROOF.md                # Coding agent documentation
│
├── design/                            # Design assets
│   ├── figma-mockups/
│   ├── portal-screenshots/
│   ├── celebration-animations/
│   └── aws-architecture-diagram.png
│
└── scripts/                           # Utility scripts
    ├── setup-dev-env.sh
    ├── seed-knowledge-base.py
    ├── test-verification.sh
    └── deploy-prod.sh
```

---

## ⚙️ CONFIGURATION FILES

### .env (Frontend)
```env
VITE_AWS_REGION=us-east-1
VITE_AWS_USER_POOL_ID=us-east-1_xxxxx
VITE_AWS_USER_POOL_CLIENT_ID=xxxxx
VITE_API_ENDPOINT=https://api.studentpathos.aws
VITE_APPSYNC_ENDPOINT=https://xxxxx.appsync-api.us-east-1.amazonaws.com/graphql
VITE_APPSYNC_API_KEY=xxxxx
VITE_ENABLE_VOICE=true
VITE_ENABLE_ANIMATIONS=true
```

### .env (Infrastructure - CDK)
```env
AWS_ACCOUNT_ID=123456789012
AWS_REGION=us-east-1
DOMAIN_NAME=studentpathos.aws
GITHUB_REPO=yourusername/studentpathos
GITHUB_BRANCH=main
BEDROCK_MODEL_ID=anthropic.claude-3-5-sonnet-20240620-v1:0
```

### tailwind.config.js
```javascript
/** @type {import('tailwindcss').Config} */
export default {
  darkMode: ["class"],
  content: [
    "./index.html",
    "./src/**/*.{ts,tsx}",
  ],
  theme: {
    extend: {
      colors: {
        border: "hsl(var(--border))",
        input: "hsl(var(--input))",
        ring: "hsl(var(--ring))",
        background: "hsl(var(--background))",
        foreground: "hsl(var(--foreground))",
        primary: {
          DEFAULT: "hsl(var(--primary))",
          foreground: "hsl(var(--primary-foreground))",
        },
        secondary: {
          DEFAULT: "hsl(var(--secondary))",
          foreground: "hsl(var(--secondary-foreground))",
        },
        destructive: {
          DEFAULT: "hsl(var(--destructive))",
          foreground: "hsl(var(--destructive-foreground))",
        },
        muted: {
          DEFAULT: "hsl(var(--muted))",
          foreground: "hsl(var(--muted-foreground))",
        },
        accent: {
          DEFAULT: "hsl(var(--accent))",
          foreground: "hsl(var(--accent-foreground))",
        },
        popover: {
          DEFAULT: "hsl(var(--popover))",
          foreground: "hsl(var(--popover-foreground))",
        },
        card: {
          DEFAULT: "hsl(var(--card))",
          foreground: "hsl(var(--card-foreground))",
        },
        // Custom colors
        'twin-primary': '#6366F1',
        'aws-orange': '#FF9900',
        'aws-squid': '#232F3E',
      },
      borderRadius: {
        lg: "var(--radius)",
        md: "calc(var(--radius) - 2px)",
        sm: "calc(var(--radius) - 4px)",
      },
      keyframes: {
        "accordion-down": {
          from: { height: "0" },
          to: { height: "var(--radix-accordion-content-height)" },
        },
        "accordion-up": {
          from: { height: "var(--radix-accordion-content-height)" },
          to: { height: "0" },
        },
        "confetti": {
          "0%": { transform: "translateY(-100%)" },
          "100%": { transform: "translateY(100vh)" },
        },
      },
      animation: {
        "accordion-down": "accordion-down 0.2s ease-out",
        "accordion-up": "accordion-up 0.2s ease-out",
        "confetti": "confetti 3s ease-in-out infinite",
      },
    },
  },
  plugins: [require("tailwindcss-animate")],
}
```

### tsconfig.json (Frontend)
```json
{
  "compilerOptions": {
    "target": "ES2020",
    "useDefineForClassFields": true,
    "lib": ["ES2020", "DOM", "DOM.Iterable"],
    "module": "ESNext",
    "skipLibCheck": true,
    
    "moduleResolution": "bundler",
    "allowImportingTsExtensions": true,
    "resolveJsonModule": true,
    "isolatedModules": true,
    "noEmit": true,
    "jsx": "react-jsx",
    
    "strict": true,
    "noUnusedLocals": true,
    "noUnusedParameters": true,
    "noFallthroughCasesInSwitch": true,
    
    "baseUrl": ".",
    "paths": {
      "@/*": ["./src/*"],
      "@components/*": ["./src/components/*"],
      "@pages/*": ["./src/pages/*"],
      "@hooks/*": ["./src/hooks/*"],
      "@stores/*": ["./src/stores/*"],
      "@services/*": ["./src/services/*"],
      "@types/*": ["./src/types/*"],
      "@utils/*": ["./src/utils/*"]
    }
  },
  "include": ["src"],
  "references": [{ "path": "./tsconfig.node.json" }]
}
```

### vite.config.ts
```typescript
import { defineConfig } from 'vite'
import react from '@vitejs/plugin-react-swc'
import path from 'path'
import svgr from 'vite-plugin-svgr'

export default defineConfig({
  plugins: [react(), svgr()],
  resolve: {
    alias: {
      '@': path.resolve(__dirname, './src'),
      '@components': path.resolve(__dirname, './src/components'),
      '@pages': path.resolve(__dirname, './src/pages'),
      '@hooks': path.resolve(__dirname, './src/hooks'),
      '@stores': path.resolve(__dirname, './src/stores'),
      '@services': path.resolve(__dirname, './src/services'),
      '@types': path.resolve(__dirname, './src/types'),
      '@utils': path.resolve(__dirname, './src/utils'),
    },
  },
  server: {
    port: 3000,
    open: true,
  },
  build: {
    outDir: 'dist',
    sourcemap: true,
  },
})
```

---

## 🔍 TESTING TOOLS

### Frontend Testing:
```bash
# Vitest (unit tests)
npm install -D vitest @vitest/ui

# React Testing Library
npm install -D @testing-library/react @testing-library/jest-dom @testing-library/user-event

# Playwright (E2E tests)
npm install -D @playwright/test
npx playwright install

# Axe Accessibility Testing
npm install -D @axe-core/playwright
```

### Backend Testing:
```bash
# Python pytest
pip install pytest pytest-cov

# AWS mocking
pip install moto boto3-stubs

# API testing
npm install -D @aws-sdk/client-apigatewaymanagementapi
```

---

## 📊 MONITORING & DEBUGGING TOOLS

```bash
# AWS X-Ray SDK (already included in Lambda runtime)
# CloudWatch Logs Insights (console-based)

# Local debugging
npm install -D @aws-sdk/client-lambda
npm install -D aws-sdk-client-mock

# Performance monitoring
npm install -D web-vitals

# Error tracking (optional)
npm install @sentry/react @sentry/tracing
```

---

## 🎯 OPTIONAL ENHANCEMENTS

### Nice-to-Have Tools:
```bash
# Storybook (component documentation)
npx storybook@latest init

# Bundle analyzer
npm install -D rollup-plugin-visualizer

# Lighthouse CI (performance)
npm install -D @lhci/cli

# Husky (git hooks)
npm install -D husky lint-staged

# Commitlint (commit message linting)
npm install -D @commitlint/{config-conventional,cli}
```

---

## 💰 COST ESTIMATION

### AWS Service Costs (Estimate for 1,000 students/month):
```
Amazon Bedrock:
  - Input tokens:  ~50M tokens  x $0.003/1K = $150
  - Output tokens: ~10M tokens  x $0.015/1K = $150
  Total: ~$300/month

Lambda:
  - Requests: ~500K invocations = $0.10
  - Compute: 500K x 1GB x 1s = ~$8
  Total: ~$8/month

DynamoDB:
  - On-demand pricing
  - Reads: 2M x $0.25/M = $0.50
  - Writes: 500K x $1.25/M = $0.63
  Total: ~$1.13/month

S3:
  - Storage: 10GB x $0.023/GB = $0.23
  - Requests: Minimal
  Total: ~$0.25/month

API Gateway:
  - Requests: 500K x $3.50/M = $1.75
  Total: ~$1.75/month

CloudFront:
  - Data transfer: 50GB x $0.085/GB = $4.25
  Total: ~$4.25/month

Step Functions:
  - State transitions: 10K x $0.025/1K = $0.25
  Total: ~$0.25/month

Other services (Cognito, Polly, AppSync): ~$10/month

TOTAL ESTIMATED COST: ~$325/month for 1,000 active students
```

### Free Tier Benefits (First 12 months):
```
- Lambda: 1M requests/month free
- DynamoDB: 25GB storage + 25 WCU/RCU free
- S3: 5GB storage + 20K GET requests free
- CloudFront: 1TB data transfer free
- API Gateway: 1M requests/month free (first 12 months)

Estimated free tier coverage: ~$50/month savings
```

---

## 🚀 DEPLOYMENT CHECKLIST

### Pre-Deployment:
- [ ] AWS account configured with credentials
- [ ] Bedrock model access approved
- [ ] Domain name registered (optional: Route 53)
- [ ] GitHub repository created
- [ ] Environment variables configured
- [ ] CDK bootstrapped

### Deployment Steps:
```bash
# 1. Clone repository
git clone <your-repo>
cd studentpathos

# 2. Install dependencies
cd frontend && npm install
cd ../infrastructure && npm install
cd ../lambda && pip install -r requirements.txt

# 3. Configure environment
cp .env.example .env
# Edit .env with your values

# 4. Build infrastructure
cd infrastructure
npm run build

# 5. Deploy (with Kiro)
cdk deploy --all --require-approval never

# 6. Seed knowledge base
python scripts/seed-knowledge-base.py

# 7. Deploy frontend
cd frontend
npm run build
aws amplify publish

# 8. Test
curl https://your-api-endpoint.aws/health
open https://studentpathos.aws
```

---

## 📚 LEARNING RESOURCES

### AWS Documentation:
- Amazon Bedrock Agents: https://docs.aws.amazon.com/bedrock/latest/userguide/agents.html
- AWS CDK Workshop: https://cdkworkshop.com/
- AWS Amplify: https://docs.amplify.aws/
- Step Functions: https://docs.aws.amazon.com/step-functions/

### React & TypeScript:
- React Docs: https://react.dev/
- TypeScript Handbook: https://www.typescriptlang.org/docs/
- Tailwind CSS: https://tailwindcss.com/docs
- Shadcn/ui: https://ui.shadcn.com/

### Best Practices:
- AWS Well-Architected Framework
- React Performance Optimization
- TypeScript Best Practices
- Accessibility (a11y) Guidelines

---

## 🐛 TROUBLESHOOTING GUIDE

### Common Issues:

**1. Bedrock Model Access Denied**
```bash
# Solution: Request model access in Bedrock console
aws bedrock list-foundation-models --region us-east-1
# Wait 5-10 minutes for approval
```

**2. CDK Bootstrap Failed**
```bash
# Solution: Ensure IAM permissions, then:
cdk bootstrap --trust <your-account-id>
```

**3. Lambda Layer Too Large**
```bash
# Solution: Use Lambda Container Images instead
# Or split dependencies across multiple layers
```

**4. API Gateway CORS Errors**
```bash
# Solution: Add proper CORS headers in CDK:
# api.addCorsPreflight(...)
```

**5. DynamoDB Throttling**
```bash
# Solution: Switch to on-demand billing mode
# Or increase provisioned capacity
```

---

**END OF REQUIREMENTS**

This document contains EVERYTHING needed to build StudentPathOS from scratch.
