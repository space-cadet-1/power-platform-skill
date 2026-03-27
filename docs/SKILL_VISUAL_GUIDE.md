# Power Platform & Dynamics 365 Management Skill
## Visual Guide - How It Works

---

## 📊 Quick Stats

| Metric | Value |
|--------|-------|
| **Lines of Documentation** | 6,454+ |
| **Complete Guides** | 12 |
| **Workflows Covered** | 50+ |
| **Installation Methods** | 4 |
| **Reference Topics** | 6 |
| **Supported Roles** | 4+ |

---

## 🎯 How It Works

```
User Asks Question
       ↓
Skill Recognizes Topic
       ↓
Skill Clarifies Role & Organization
       ↓
Skill Provides Tailored Guidance
       ↓
User Gets Exactly What They Need
```

### The Process - 3 Simple Steps

#### 1️⃣ Task Recognition
When you ask about a Power Platform or D365 task, the skill identifies which topic area:
- Environment Management
- Solution Deployment  
- Security & Permissions
- Data Operations
- Integrations
- D365 FO Development
- Pre-Deployment Validation

#### 2️⃣ Role Clarification
The skill learns your role, which determines approvals and access:
- **Dynamics Admin/Developer** — Full access, no approvals
- **Power Platform Manager** — Solutions & security with approvals
- **Team Lead** — Team-level permissions with approvals
- **Power User** — Forms & customizations with limited access

#### 3️⃣ Personalized Guidance
Based on your role, task, and organization context, you get:
- ✓ Step-by-step workflows with decision points
- ✓ Real-world examples and edge case handling
- ✓ Checklists to verify you're on track
- ✓ Troubleshooting guides if you get stuck
- ✓ Templates and code samples to reuse
- ✓ Approval requirements and governance rules

---

## 👥 User Journey

### The Five Stages

| Stage | What Happens | Example |
|-------|-------------|---------|
| **① User Action** | User asks about their task | "I need to deploy a solution to production" |
| **② Recognition** | Skill identifies the topic | Deployment workflow detected |
| **③ Clarification** | Skill asks about role & org | "Are you an admin? What's your version format?" |
| **④ Customization** | Preferences are stored | Version = 1.0.YYYYMM, Role = Admin |
| **⑤ Guidance** | Personalized step-by-step help | 7-step workflow, checklists, validation |

### Result
Users go from **confused → informed → confident** in **15-45 minutes** depending on task complexity.

---

## 🏗️ Information Architecture

The skill organizes information into three main pathways:

### 📚 Quick Start Documents
**Get oriented in 5-15 minutes**

For users who are lost or confused:
- **START_HERE.txt** — Choose your path (5 min)
- **QUICK_REFERENCE.md** — One-page cheat sheet (5 min)
- **README.md** — Product overview (10 min)

### 📖 Reference Documents  
**Deep dives by topic**

For users who know their task:
- **SKILL.md** — Main entry point with all workflows
- **d365-fo-development.md** — Claude Code & X++ development
- **data-operations.md** — CSV/XML import & validation
- **entity-management.md** — Creating entities & forms
- **integrations.md** — SharePoint & qualification workflows
- **security-roles.md** — Teams, business units, permissions

### 🛠️ Tools & Examples
**Practical utilities**

- **Python Scripts** — Installation & validation
- **Templates** — Reusable starting points
- **Checklists** — Pre-deployment validation
- **Examples** — Real-world scenarios

### How Users Navigate

```
Confused User Path:
START_HERE.txt → QUICK_REFERENCE → Find Task → Reference Doc → Step-by-Step Guide

Specific Task Path:
QUICK_REFERENCE → Find Task → Jump to Reference → Get Instructions

Deep Learning Path:
README.md → SKILL.md → Reference Docs → Examples → Advanced Topics
```

---

## 🎭 Real User Scenarios

### Scenario 1: System Admin Deploying a Solution

**User Says:** "I need to deploy this solution to production"

**Skill Recognizes:** Deployment workflow, admin role (no approvals needed)

**Skill Provides:**
- Environment sanitization checklist
- Version number guidance
- 7-step deployment workflow
- Pre-deployment checklist (admin version)
- Rollback procedures
- Post-deployment validation

---

### Scenario 2: D365 FO Developer Requesting Code Review

**User Says:** "Can you review my X++ code for performance?"

**Skill Recognizes:** Code review task, D365 FO context, developer role

**Skill Provides:**
- Structured code review checklist
- Extension vs overlayering guidance
- Performance analysis
- Security concerns
- TTS boundaries
- Error handling review
- Test recommendations

---

### Scenario 3: Power Platform Manager Managing Security Roles

**User Says:** "Help me set up security roles for my customer service team"

**Skill Recognizes:** Security management, manager role (team-level focus)

**Skill Provides:**
- Critical rule (never individual assignments)
- Team-based setup guide
- Permission depth level explanation
- Custom role template
- Troubleshooting guide
- Approval workflows
- Documentation requirements

---

### Scenario 4: Confused User With No Context

**User Says:** "I don't know where to start"

**Skill Recognizes:** User needs orientation, no task or role specified

**Skill Provides:**
- START_HERE.txt guide
- "Choose your path" questions
- Quick reference lookup
- Full topic index
- Time estimates
- Clear next steps

---

## ✨ Key Features & Benefits

| Feature | Benefit | Who Benefits |
|---------|---------|--------------|
| **Role-Based Guidance** | Admins skip approvals, Managers see workflows | Everyone gets relevant guidance |
| **Multiple Entry Points** | Start anywhere - no wrong answer | Confused users get oriented instantly |
| **Task-Specific Help** | Find exactly what you need in seconds | Experienced users stay in flow |
| **Stored Preferences** | Version format & conventions remembered | Consistent, personalized guidance |
| **Step-by-Step Workflows** | Clear procedures for every major task | No guessing, no searching |
| **Real-World Examples** | Learn from practical scenarios | Understand context & rationale |
| **Troubleshooting Guides** | Common issues with solutions | Unblock yourself quickly |
| **Checklists & Templates** | Reusable starting points | Faster execution, better quality |
| **Pre-Deployment Validation** | Catch issues before production | Prevent incidents |
| **D365 FO Development** | Claude Code integration | Accelerate development |

---

## 🚀 Getting Started

### Choose Your Entry Point

#### If You're Confused
Start with **START_HERE.txt** or **QUICK_REFERENCE.md**

These will orient you and point to the right reference material in **5-15 minutes**.

#### If You Know Your Task
Open **QUICK_REFERENCE.md** and find your task in the quick lookup table.

It will tell you exactly which reference document to read.

#### If You Want Comprehensive Understanding
Start with **README.md**, then **SKILL.md**, then specific reference documents.

### Key Resources at a Glance

| For... | Read This | Time |
|--------|-----------|------|
| Quick answers | QUICK_REFERENCE.md | 5 min |
| Overview | README.md or START_HERE.txt | 5-15 min |
| Step-by-step | SKILL.md or reference docs | 15-45 min |
| Templates | Examples folder | 5-10 min |
| Troubleshooting | Reference doc section | 5-15 min |

### Tips for Best Results

✓ **Test in Dev first** — Always validate in Dev before higher environments

✓ **Use the checklists** — Pre-deployment checklists catch issues early

✓ **Store your preferences** — Document version format, naming conventions, team structure

✓ **Save templates** — Customize once, reuse many times

✓ **Ask for clarification** — The skill is helpful and can explain anything

✓ **Bookmark & reference** — Keep QUICK_REFERENCE.md handy for fast lookups

---

## 🎓 What You'll Learn

By using this skill, you'll understand:

- ✓ How to structure and manage Power Platform environments
- ✓ The complete solution deployment lifecycle
- ✓ How to implement security roles correctly (teams, not individuals)
- ✓ Data import/export best practices
- ✓ How to set up integrations (SharePoint, Power Automate, etc.)
- ✓ D365 FO development patterns and best practices
- ✓ Pre-deployment validation and risk mitigation
- ✓ Troubleshooting common issues
- ✓ Creating reusable templates and processes

---

## 📞 Support

### Getting Help

1. **Read** — Start with QUICK_START.md or START_HERE.txt
2. **Search** — Check FAQ.md or QUICK_REFERENCE.md
3. **Explore** — Browse the skill/SKILL.md for your topic
4. **Troubleshoot** — Check the troubleshooting section of any reference doc

### Common Entry Points

- **Confused?** → START_HERE.txt
- **Need quick answer?** → QUICK_REFERENCE.md
- **Want overview?** → README.md
- **Need detailed guide?** → SKILL.md or reference docs
- **Looking for template?** → Examples folder

---

## 🎯 Next Steps

1. **Read START_HERE.txt** (5 minutes) — Get oriented
2. **Check QUICK_REFERENCE.md** (5 minutes) — Find your task
3. **Open relevant reference doc** (15-45 minutes) — Get detailed guidance
4. **Use checklist** — Verify you're on track
5. **Ask for help** — The skill is here to assist

---

## 📈 Success Metrics

After using this skill, you should be able to:

✓ Understand your role in the organization  
✓ Know what approvals you need before deploying  
✓ Follow a clear step-by-step process for your task  
✓ Use checklists to verify you're ready  
✓ Troubleshoot issues when they arise  
✓ Explain your decisions to stakeholders  
✓ Avoid common mistakes  
✓ Complete your task confidently  

---

## 📚 Documentation Structure

```
skill/
├── SKILL.md (Main entry point)
├── START_HERE.txt (Quick orientation)
├── QUICK_REFERENCE.md (One-page lookup)
├── README.md (Product overview)
└── references/
    ├── d365-fo-development.md
    ├── data-operations.md
    ├── entity-management.md
    ├── integrations.md
    └── security-roles.md
```

---

## 💡 Key Takeaways

| Principle | Why It Matters |
|-----------|-----------------|
| **Role-based** | You see only what applies to your role |
| **Task-focused** | Find what you need instantly, not buried |
| **Multiple pathways** | Start anywhere, move at your own pace |
| **Practical guidance** | Learn how to do it, not just theory |
| **Real examples** | See how this works in practice |
| **Troubleshooting** | Get help when you're stuck |
| **Personalization** | Guidance tailored to your organization |

---

## 🔗 Quick Links

- [Installation Guide](docs/INSTALLATION.md)
- [Quick Start](docs/QUICK_START.md)
- [Main Skill](skill/SKILL.md)
- [Quick Reference](QUICK_REFERENCE.md)
- [GitHub Upload Guide](docs/GITHUB_UPLOAD_GUIDE.md)

---

## 📝 Document Information

**Created:** 2024  
**Last Updated:** March 26, 2026  
**Version:** 1.0  
**Format:** Markdown + Visual Diagrams  
**Status:** Production Ready  

---

**Ready to get started?** Open **START_HERE.txt** and begin your journey!
