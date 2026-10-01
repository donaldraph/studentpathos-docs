# 🎨 Professional Design & Frontend Tools Guide

## 📦 CURRENTLY INSTALLING (Background Process)

All professional design and development tools are being installed. You'll be notified when complete!

---

## 🎯 TOOLS OVERVIEW

### **1. DESIGN & VISUAL TOOLS**

#### **SVG Optimization & Manipulation**
```bash
# Optimize SVG files (reduce size, clean up)
svgo input.svg -o output.svg

# Convert SVG to React component
npx @svgr/cli --icon --typescript icon.svg > Icon.tsx
```

#### **Image Processing**
```bash
# Resize image
sharp resize 800 600 input.png -o output.png

# Convert format
sharp convert input.png -o output.webp

# Generate responsive images
sharp resize 400 300 input.png -o thumb.png
sharp resize 1200 800 input.png -o large.png
```

#### **Beautiful Code Screenshots** (For Demo/Documentation)
```bash
# Create beautiful code screenshot
carbon-now src/App.tsx --save-to ./screenshots

# With custom theme
carbon-now src/App.tsx --theme dracula --save-to ./screenshots
```

#### **Diagram Generation**
```bash
# Create Mermaid diagram from code
mmdc -i diagram.mmd -o diagram.png

# Example diagram.mmd:
# graph TD
#   A[Student] --> B[AI Twin]
#   B --> C[AWS Services]
#   C --> D[Verification]
```

#### **ASCII Art & Terminal Graphics**
```bash
# Generate ASCII art text
figlet "StudentPathOS"

# Create ASCII diagrams
graph-easy <<< "A -> B -> C"
```

---

### **2. COMPONENT DEVELOPMENT**

#### **Storybook** (Component Playground)
```bash
# Start Storybook
npm run storybook
# Opens at http://localhost:6006

# Build static Storybook (for deployment)
npm run build-storybook
```

**Create a story:**
```typescript
// src/components/TwinChat.stories.tsx
import type { Meta, StoryObj } from '@storybook/react'
import { TwinChat } from './TwinChat'

const meta: Meta<typeof TwinChat> = {
  title: 'Components/TwinChat',
  component: TwinChat,
  tags: ['autodocs'],
}

export default meta
type Story = StoryObj<typeof TwinChat>

export const Default: Story = {
  args: {
    studentName: 'Sarah',
    messages: [],
  },
}

export const WithMessages: Story = {
  args: {
    studentName: 'Sarah',
    messages: [
      { role: 'user', content: 'What is Builder Center?' },
      { role: 'assistant', content: 'Builder Center is...' },
    ],
  },
}
```

#### **Ladle** (Faster Storybook Alternative)
```bash
# Start Ladle
npx ladle serve

# Build for production
npx ladle build
```

---

### **3. CODE QUALITY**

#### **Linting**
```bash
# Run ESLint
npm run lint

# Auto-fix issues
npm run lint:fix

# Check specific file
npx eslint src/components/TwinChat.tsx
```

#### **Formatting**
```bash
# Format all code
npm run format

# Check formatting
npm run format:check

# Format specific file
npx prettier --write src/App.tsx
```

#### **Type Checking**
```bash
# Check TypeScript types
npm run type-check

# Watch mode
npm run type-check -- --watch
```

#### **Git Hooks** (Auto-run on commit)
```bash
# Pre-commit hook runs automatically:
# - ESLint on staged .ts/.tsx files
# - Prettier formatting
# - Stylelint on CSS

# To skip hooks (emergency only):
git commit --no-verify
```

---

### **4. ACCESSIBILITY TESTING**

#### **Axe** (In-code accessibility checks)
```typescript
// In your tests
import { axe, toHaveNoViolations } from 'jest-axe'

expect.extend(toHaveNoViolations)

test('TwinChat should have no accessibility violations', async () => {
  const { container } = render(<TwinChat />)
  const results = await axe(container)
  expect(results).toHaveNoViolations()
})
```

#### **Pa11y** (Live URL accessibility audit)
```bash
# Check accessibility of running app
npm run a11y

# Check specific page
pa11y http://localhost:3000/dashboard

# Generate report
pa11y --reporter html http://localhost:3000 > a11y-report.html
```

---

### **5. PERFORMANCE TESTING**

#### **Lighthouse** (Full performance audit)
```bash
# Audit running app
npm run lighthouse

# Or manually
lighthouse http://localhost:3000 --view

# Generate JSON report
lighthouse http://localhost:3000 --output json --output-path report.json

# Mobile simulation
lighthouse http://localhost:3000 --preset=mobile --view
```

#### **Bundle Analysis**
```bash
# Analyze bundle size
npm run analyze

# Check size limits
npm run size
```

**What to look for:**
- Total bundle < 500KB
- First Contentful Paint < 1.8s
- Time to Interactive < 3.8s
- Cumulative Layout Shift < 0.1

---

### **6. TESTING**

#### **Unit Tests (Vitest)**
```bash
# Run tests
npm run test

# Watch mode
npm run test -- --watch

# Coverage
npm run test:coverage

# UI mode
npm run test:ui
```

#### **E2E Tests (Playwright)**
```bash
# Run all E2E tests
npm run test:e2e

# UI mode (interactive)
npm run test:e2e:ui

# Specific browser
npx playwright test --project=chromium

# Debug mode
npx playwright test --debug

# Generate tests (record actions)
npx playwright codegen http://localhost:3000
```

**Example E2E test:**
```typescript
// tests/e2e/student-journey.spec.ts
import { test, expect } from '@playwright/test'

test('student can complete onboarding journey', async ({ page }) => {
  await page.goto('/')
  
  // Click "Get Started"
  await page.click('text=Get Started')
  
  // Verify dashboard loads
  await expect(page.locator('h1')).toContainText('Your Journey')
  
  // Check progress bar
  const progress = await page.locator('[role="progressbar"]')
  await expect(progress).toHaveAttribute('aria-valuenow', '20')
})
```

---

### **7. ANIMATION TOOLS**

#### **Lottie Animations**
```bash
# Download from https://lottiefiles.com
# Place in: public/celebration-assets/confetti.json
```

```typescript
// Use in React
import Lottie from 'lottie-react'
import confettiAnimation from '@/public/celebration-assets/confetti.json'

function Celebration() {
  return <Lottie animationData={confettiAnimation} loop={false} />
}
```

#### **Confetti**
```typescript
import confetti from 'canvas-confetti'

function celebrate() {
  confetti({
    particleCount: 100,
    spread: 70,
    origin: { y: 0.6 }
  })
}
```

#### **Framer Motion** (Already installed)
```typescript
import { motion } from 'framer-motion'

<motion.div
  initial={{ opacity: 0, y: 20 }}
  animate={{ opacity: 1, y: 0 }}
  transition={{ duration: 0.5 }}
>
  Content here
</motion.div>
```

---

### **8. UI DEVELOPMENT**

#### **React Query Devtools**
```typescript
// Add to App.tsx
import { ReactQueryDevtools } from '@tanstack/react-query-devtools'

function App() {
  return (
    <>
      <YourApp />
      <ReactQueryDevtools initialIsOpen={false} />
    </>
  )
}
```

#### **React Hook Form Devtools**
```typescript
import { DevTool } from '@hookform/devtools'

function MyForm() {
  const { control } = useForm()
  
  return (
    <>
      <form>...</form>
      <DevTool control={control} />
    </>
  )
}
```

---

### **9. ICON TOOLS**

#### **Lucide React** (Primary icon set)
```typescript
import { Check, X, AlertCircle } from 'lucide-react'

<Check className="text-green-500" />
<X className="text-red-500" />
<AlertCircle className="text-yellow-500" />
```

#### **Iconify** (16,000+ icons)
```typescript
import { Icon } from '@iconify/react'

<Icon icon="mdi:aws" />
<Icon icon="simple-icons:react" />
<Icon icon="logos:amazon-web-services" />
```

---

### **10. DEVELOPMENT UTILITIES**

#### **HTTPie** (API Testing)
```bash
# GET request
http GET https://api.studentpathos.aws/health

# POST with JSON
http POST https://api.studentpathos.aws/chat \
  message="Hello" \
  student_id="123"

# With authentication
http GET https://api.studentpathos.aws/profile \
  Authorization:"Bearer token"
```

#### **FX** (JSON viewer)
```bash
# Pretty print JSON
echo '{"name":"StudentPathOS"}' | fx

# Interactive JSON explorer
cat response.json | fx
```

#### **Serve** (Quick static server)
```bash
# Serve dist folder
serve dist

# Custom port
serve -p 8000 dist
```

#### **Netlify CLI** (Preview deployments)
```bash
# Login
netlify login

# Deploy preview
netlify deploy

# Deploy production
netlify deploy --prod
```

---

## 🎨 DESIGN WORKFLOW FOR HACKATHON

### **Phase 1: Component Design (Storybook)**
```bash
# 1. Start Storybook
npm run storybook

# 2. Create component with story
# src/components/JourneyTimeline.tsx
# src/components/JourneyTimeline.stories.tsx

# 3. Design in isolation
# - Try different states
# - Test responsive behavior
# - Verify accessibility

# 4. Export Storybook (for demo)
npm run build-storybook
```

### **Phase 2: Integration Testing (Playwright)**
```bash
# 1. Record user flow
npx playwright codegen http://localhost:3000

# 2. Save as test
# tests/e2e/onboarding.spec.ts

# 3. Run tests
npm run test:e2e

# 4. Generate HTML report
npx playwright show-report
```

### **Phase 3: Performance Audit**
```bash
# 1. Build production
npm run build

# 2. Serve production build
serve dist

# 3. Run Lighthouse
npm run lighthouse

# 4. Analyze bundle
npm run analyze

# 5. Check size limits
npm run size
```

### **Phase 4: Accessibility Check**
```bash
# 1. Run Pa11y
npm run a11y

# 2. Fix violations
# (Check console output)

# 3. Verify with axe in tests
npm run test -- --coverage

# 4. Manual keyboard navigation test
# - Tab through all interactive elements
# - Verify focus indicators
# - Test screen reader (NVDA/VoiceOver)
```

---

## 🎯 QUALITY CHECKLIST (Before Demo)

### **Code Quality**
- [ ] `npm run lint` - No errors
- [ ] `npm run format:check` - All files formatted
- [ ] `npm run type-check` - No TypeScript errors
- [ ] `npm run test` - All tests passing
- [ ] `npm run test:coverage` - >80% coverage

### **Performance**
- [ ] `npm run lighthouse` - Score >90
- [ ] `npm run analyze` - Bundle <500KB
- [ ] `npm run size` - Within limits
- [ ] First paint <1.8s
- [ ] Interactive <3.8s

### **Accessibility**
- [ ] `npm run a11y` - No violations
- [ ] Keyboard navigation works
- [ ] Screen reader tested
- [ ] Color contrast >4.5:1
- [ ] ARIA labels present

### **Browser Testing**
- [ ] Chrome (desktop)
- [ ] Firefox (desktop)
- [ ] Safari (desktop)
- [ ] Chrome (mobile)
- [ ] Safari (iOS)

### **E2E Testing**
- [ ] Happy path works
- [ ] Error states handled
- [ ] Loading states shown
- [ ] Edge cases covered

---

## 📸 CREATING DEMO ASSETS

### **Screenshots for Documentation**
```bash
# 1. Beautiful code screenshots
carbon-now src/components/TwinChat.tsx \
  --theme dracula \
  --save-to ./docs/screenshots

# 2. Full page screenshots (Playwright)
npx playwright screenshot http://localhost:3000 homepage.png

# 3. Component screenshots (Storybook)
# Built-in: Storybook has screenshot addon
```

### **Architecture Diagrams**
```bash
# 1. Create Mermaid diagram
cat > architecture.mmd << 'EOF'
graph TB
  A[Student] --> B[React Frontend]
  B --> C[API Gateway]
  C --> D[Bedrock Agent]
  D --> E[Lambda Tools]
  E --> F[DynamoDB]
EOF

# 2. Generate PNG
mmdc -i architecture.mmd -o architecture.png -w 1200
```

### **Demo Video Assets**
```bash
# 1. Record terminal session
# (Use OBS Studio or screen recording)

# 2. Add captions
# (Use Kapwing or similar)

# 3. Generate thumbnail
# (Use Canva or Figma)
```

---

## 🚀 DEPLOYMENT CHECKLIST

### **Before Deploy**
```bash
# 1. Run all quality checks
npm run lint
npm run format:check
npm run type-check
npm run test
npm run lighthouse
npm run a11y
npm run size

# 2. Build production
npm run build

# 3. Test production build locally
serve dist
# Open http://localhost:3000

# 4. Verify bundle size
ls -lh dist/

# 5. Check for console errors
# (Open DevTools in served build)
```

### **Deploy to Netlify**
```bash
# Option 1: Via Git (Recommended)
git push origin main
# Netlify auto-deploys

# Option 2: Manual deploy
netlify deploy --prod

# Option 3: Drag & drop
# Upload dist/ folder to Netlify UI
```

### **Deploy to AWS Amplify**
```bash
# Via CDK (already configured)
cd ~/builds/studentpathos/infrastructure
cdk deploy FrontendStack
```

---

## 💡 PRO TIPS

### **Faster Development**
```bash
# Use Vite's hot reload
npm run dev
# Changes reflect instantly

# Component development in Storybook
npm run storybook
# Faster than full app reload
```

### **Debug Performance Issues**
```bash
# 1. Check bundle composition
npm run analyze

# 2. Find large dependencies
npx vite-bundle-visualizer

# 3. Profile in browser
# DevTools → Performance → Record
```

### **Fix Common Issues**

**"Module not found"**
```bash
# Clear node_modules and reinstall
rm -rf node_modules package-lock.json
npm install
```

**"Port already in use"**
```bash
# Find process
lsof -i :3000

# Kill process
kill -9 <PID>
```

**"Out of memory"**
```bash
# Increase Node memory
NODE_OPTIONS=--max-old-space-size=4096 npm run build
```

---

## 📚 USEFUL RESOURCES

### **Documentation**
- Vite: https://vitejs.dev/
- React: https://react.dev/
- Tailwind: https://tailwindcss.com/
- Storybook: https://storybook.js.org/
- Playwright: https://playwright.dev/
- Vitest: https://vitest.dev/

### **Design Inspiration**
- Dribbble: https://dribbble.com/tags/dashboard
- Awwwards: https://www.awwwards.com/
- UI Design Daily: https://www.uidesigndaily.com/

### **Accessibility**
- WCAG Guidelines: https://www.w3.org/WAI/WCAG21/quickref/
- A11y Project: https://www.a11yproject.com/
- WebAIM: https://webaim.org/

### **Performance**
- Web.dev: https://web.dev/measure/
- Chrome DevTools: https://developer.chrome.com/docs/devtools/

---

## 🎬 READY TO CREATE!

All tools are installed and configured. You're equipped to build a **competition-winning** frontend!

**Next steps:**
1. Wait for installation to complete (background process)
2. Tell me your idea so we can start building
3. I'll use these tools to create professional-grade UI

**Installation progress:**
```bash
# Check status
tail -f ~/design-tools-install.log
```

🎨 **You're ready to build something beautiful!** 🚀
