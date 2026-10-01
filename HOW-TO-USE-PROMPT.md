# How to Use the Comprehensive Build Prompt

## ✅ What I Just Created For You

I've created a **complete, self-contained prompt** at:
```
~/COMPREHENSIVE-BUILD-PROMPT.md
```

This prompt contains EVERYTHING needed to build StudentPathOS from scratch:
- Complete project overview & goals
- Full system architecture (Bedrock, Lambda, DynamoDB, Step Functions, etc.)
- Step-by-step build instructions for all 7 days
- Code examples for every component
- Commit message style (human, not robotic)
- Documentation style (human, not corporate)
- Git authorship configuration (donaldraph only)
- GitHub setup instructions
- Coding agent proof requirements
- Quality checklists
- Demo preparation guide

## 🎯 How to Use This Prompt

### Option 1: Paste Into Claude (Recommended)

1. **Open the prompt file:**
   ```bash
   cat ~/COMPREHENSIVE-BUILD-PROMPT.md
   ```

2. **Copy EVERYTHING after the line:**
   ```
   ---
   ```

3. **Start a NEW Claude conversation** (fresh context)

4. **Paste the entire prompt**

5. **Send this follow-up message:**
   ```
   Start building Day 1: Core Agent + Knowledge Base
   
   Remember:
   - Git author: donaldraph
   - GitHub repo: https://github.com/donaldraph/studentpathos
   - Commit often with human messages
   - All commits: "built with claude code via kiro"
   ```

6. **Claude will start building** step-by-step

### Option 2: Use With Claude Code (Kiro)

```bash
# In terminal with Claude Code
claude code

# Then paste the prompt and say:
# "Build this project using the instructions above"
```

### Option 3: Split Into Phases

If Claude context runs out, split by day:

**Day 1:**
```
Read ~/COMPREHENSIVE-BUILD-PROMPT.md

Build Phase 1 (Day 1): Core Agent + Knowledge Base
- Bedrock Agent setup
- 3 core Lambda tools
- DynamoDB tables
- Basic React chat interface

Git config: user.name="donaldraph"
Commit often, human style
```

**Day 2:**
```
Continue StudentPathOS build

Build Phase 2 (Day 2): Visual Intelligence
- Screenshot analysis tool
- Portal comparison component
- Image upload flow

Keep committing as donaldraph
```

(And so on for each day)

## 📝 What to Tell Claude

When you paste the prompt, Claude might ask questions. Here's what to clarify:

**"Should I start building now?"**
→ "Yes, start with Day 1: Core Agent + Knowledge Base"

**"Do you want me to create the GitHub repo?"**
→ "Yes, but create it locally first, I'll push to GitHub manually"
OR
→ "Yes, create it and I'll provide my GitHub token"

**"Should I use mock data or real AWS integration?"**
→ "Start with mock data for speed, add real AWS checks on Day 4"

**"How much of each component should I build?"**
→ "Build working MVP first, then enhance. Function over form initially."

## 🎯 Key Points to Emphasize

When working with Claude, remind it:

1. **Git authorship is CRITICAL:**
   ```bash
   # Every commit must show:
   Author: donaldraph <donaldraph@users.noreply.github.com>
   
   # Check with:
   git log --pretty=format:"%an <%ae>" | head -20
   ```

2. **Commit messages must be human:**
   ```
   GOOD: "chat interface working, took forever to get animations right"
   BAD: "feat: implement chat interface with animations"
   ```

3. **Commit frequently:**
   ```
   # Every 20-30 min of work
   # NOT once at the end
   ```

4. **Include agent attribution:**
   ```
   Every commit ends with:
   
   built with claude code via kiro
   ```

5. **GitHub repository:**
   ```
   https://github.com/donaldraph/studentpathos
   Push regularly to show progression
   ```

## 🚨 Common Issues & Solutions

### Issue: Claude says "I can't create GitHub repos"
**Solution:** 
```bash
# Create repo manually on GitHub first
# Then tell Claude: "I created the repo, here's the URL: ..."
```

### Issue: Git authorship shows wrong name
**Solution:**
```bash
cd ~/builds/studentpathos
git config user.name "donaldraph"
git config user.email "donaldraph@users.noreply.github.com"

# Fix last commit if needed:
git commit --amend --reset-author --no-edit
```

### Issue: Claude makes commits with Co-authored-by
**Solution:**
```
Tell Claude: "Remove all Co-authored-by lines. Single author only: donaldraph"
```

### Issue: Commits are too infrequent
**Solution:**
```
Tell Claude: "Commit after every feature, not at the end. I need to see progression."
```

### Issue: Commit messages are too formal
**Solution:**
```
Tell Claude: "Write commit messages like a human, not a robot. Casual, authentic, show personality."

Examples:
- "finally got the confetti animation working, looks sick"
- "refactored twin chat, much cleaner now"
- "added voice support, polly integration was easier than expected"
```

## 📊 Expected Output

After using this prompt, you should have:

1. **Git Repository:**
   - 100+ commits over 7 days
   - All authored by donaldraph
   - Human-style commit messages
   - Regular pushes to GitHub

2. **Working Application:**
   - Live URL (Amplify deployment)
   - Bedrock Agent responding
   - Journey dashboard tracking
   - Visual portal comparison
   - Mobile responsive
   - Accessibility compliant

3. **Documentation:**
   - README.md (human-readable)
   - ARCHITECTURE.md (explains design)
   - Setup instructions tested
   - Demo video (5 min)

4. **Coding Agent Proof:**
   - CloudTrail logs
   - Git commits with attribution
   - Video of agent building
   - Document explaining process

5. **Demo Assets:**
   - 5-minute video
   - Architecture diagram
   - Screenshots
   - Metrics slide

## ⏰ Timeline

**Day 1-3:** Core functionality (chat, dashboard, visual tools)  
**Day 4-5:** Advanced features (orchestration, analytics)  
**Day 6:** Polish (voice, celebrations, animations)  
**Day 7:** Deploy, document, demo prep

**Total:** 7 days to complete MVP + documentation + demo

## 🎯 Success Criteria

You'll know it's working if:

✅ You can chat with the AI twin  
✅ Dashboard shows 5-step journey progress  
✅ Visual portal comparison loads  
✅ Mobile works (test on phone)  
✅ Git log shows donaldraph as author  
✅ Commits are frequent and human  
✅ Live URL accessible  
✅ Demo video recorded  

## 💡 Pro Tips

1. **Start simple:** Get basic chat working first, then enhance
2. **Test continuously:** Don't wait until Day 7
3. **Commit often:** Show your work progression
4. **Document as you go:** Not at the end
5. **Mobile test early:** Don't discover issues on Day 7
6. **Record progress:** Take screenshots/videos along the way

## 🚀 Ready to Build?

1. Copy the prompt from `COMPREHENSIVE-BUILD-PROMPT.md`
2. Paste into new Claude conversation
3. Say: "Start building Day 1"
4. Let Claude work, supervise authorship
5. Ship by October 2, 2026!

---

**Questions?**
- Check the main prompt for detailed instructions
- Review code examples in the prompt
- Follow the 7-day build plan
- Verify authorship frequently

**Good luck building StudentPathOS!** 🎉
