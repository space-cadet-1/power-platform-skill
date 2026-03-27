# Power Platform & Dynamics 365 Management Skill

![GitHub License](https://img.shields.io/badge/license-MIT-blue.svg)
![Version](https://img.shields.io/badge/version-1.0.0-green.svg)
![Status](https://img.shields.io/badge/status-production%20ready-brightgreen.svg)
![Python](https://img.shields.io/badge/python-3.8%2B-blue.svg)

A comprehensive Claude skill for managing Microsoft Dynamics 365 and Power Platform environments, with integrated D365 FO development acceleration using Claude Code.

---

## 🎯 What This Skill Does

This skill provides expert guidance on:

- **Environment Management** — Create and configure Power Platform environments
- **Solution Deployment** — Deploy solutions across Dev → Test → PreProd → Prod with version tracking
- **Security & Permissions** — Manage teams, business units, and custom security roles
- **Data Operations** — Import/export CSV and XML with validation and deduplication
- **Integrations** — Set up SharePoint sync and qualification expiration workflows
- **D365 FO Development** — Accelerate X++ development with Claude Code, code review, and testing
- **Pre-Deployment Validation** — Role-based checklists before production deployments

---

## 📊 Visual Guide: How The Skill Works

### User Journey & Skill Response

```
┌──────────────────────────────────────────────────────────────┐
│                    How The Skill Works                       │
│            User Ask → Recognition → Guidance → Help          │
└──────────────────────────────────────────────────────────────┘

① USER ACTION
   "I need to deploy a solution to production"
              ↓
② SKILL RECOGNITION
   Detects: Deployment workflow, Admin role
              ↓
③ CLARIFICATION
   Asks: What's your org? What's your version format?
              ↓
④ CUSTOMIZATION
   Stores: Version format = 1.0.YYYYMM, Role = Admin
              ↓
⑤ PERSONALIZED GUIDANCE
   Provides: 7-step workflow, checklists, rollback plan
```

### Information Architecture: How Files Are Organized

```
                    SKILL.md (Main Entry Point)
                            ↓
            ┌───────────────┼───────────────┐
            ↓               ↓               ↓
    ┌─────────────┐  ┌──────────────┐  ┌──────────────┐
    │Quick Start  │  │ Reference    │  │Tools &       │
    │(5-15 min)   │  │ Docs         │  │Examples      │
    └─────────────┘  │(Deep dives)  │  │(Utilities)   │
    ├─START_HERE.txt │          │  │              │
    ├─QUICK_REF.md   ├─Environment  ├─Python Scripts
    └─README.md      ├─Deployment   ├─Templates
                     ├─Security     └─Checklists
                     ├─Data Ops
                     ├─Integrations
                     └─D365 FO Dev
```

### User Scenarios: Real-World Examples

**Scenario 1: System Admin Deploying**
```
USER:   "I need to deploy this solution to production"
SKILL:  Recognizes → Admin role (no approvals)
GIVES:  7-step workflow, sanitization checklist, rollback plan
```

**Scenario 2: D365 FO Developer**
```
USER:   "Can you review my X++ code?"
SKILL:  Recognizes → Code review context
GIVES:  Review checklist, performance analysis, test recommendations
```

**Scenario 3: Power Platform Manager**
```
USER:   "Help me set up security roles for my team"
SKILL:  Recognizes → Manager role (team-level focus)
GIVES:  Team setup guide, permission templates, approval workflows
```

**Scenario 4: Confused User**
```
USER:   "I don't know where to start"
SKILL:  Recognizes → Needs orientation
GIVES:  START_HERE.txt, choose your path, quick reference
```

---

## ⭐ Key Features

✅ **Role-Based Guidance** — Different workflows for Admin, Developer, Manager, Power User  
✅ **Persistent Preferences** — Remembers your version format and naming conventions  
✅ **Step-by-Step Workflows** — Complete guidance for every major task  
✅ **Real-World Examples** — Practical scenarios with decision trees  
✅ **Reusable Templates** — Approval requests, checklists, role definitions  
✅ **Troubleshooting Guides** — Solutions for common issues and error diagnosis  
✅ **D365 FO Acceleration** — Claude Code prompts and development workflows  
✅ **Browser Extension Ready** — Works seamlessly with Claude's tools  

---

## 📦 Package Contents

### Documentation (6,454+ lines)
- **SKILL.md** — Main skill with all workflows
- **6 Reference Guides** — Deep dives by topic:
  - Environment Management
  - Solution Deployment & Versioning
  - Security & Permissions
  - Data Operations
  - Integrations
  - D365 FO Development
- **Pre-Deployment Checklist** — Role-based validation
- **Quick Reference** — One-page lookup tables

### Python Utilities
- **install.py** (700 lines) — Automated installation
- **validate.py** (500 lines) — Installation validation

### Documentation
- **4 Installation Methods** — Automated, Manual, Docker, Development
- **GitHub Upload Guide** — Step-by-step instructions
- **FAQ** — Common questions
- **Contributing Guidelines** — How to help

### Visual Guides (3 Formats)
- **PDF** — Professional 8-page printable guide
- **HTML** — Interactive web version
- **Markdown** — GitHub-friendly format

---

## 🚀 Quick Start

### Installation

```bash
# Fastest way: Automated installation
python scripts/install.py

# Or: Manual installation
mkdir -p ~/.claude-skills/power-platform
cp -r skill/* ~/.claude-skills/power-platform/
```

See [Installation Guide](docs/INSTALLATION.md) for 4 complete methods.

### First Time Using

1. **Read the Quick Reference** (5 minutes)
   ```bash
   cat QUICK_REFERENCE.md
   ```

2. **Choose Your Path** (10 minutes)
   - System Administrator? → See Security & Permissions
   - D365 FO Developer? → See D365 FO Development
   - Power Platform Manager? → See Solution Deployment

3. **Use the Skill**
   - Import into Claude.ai or Claude Code
   - Ask for help with your task
   - Get step-by-step guidance

---

## 📚 Documentation

| Document | Purpose | Time |
|----------|---------|------|
| [INSTALLATION.md](docs/INSTALLATION.md) | How to install (4 methods) | 10 min |
| [QUICK_START.md](docs/QUICK_START.md) | Get started in 5 minutes | 5 min |
| [SKILL_OVERVIEW.md](docs/SKILL_OVERVIEW.md) | What the skill does | 10 min |
| [FAQ.md](docs/FAQ.md) | Common questions | 5 min |
| [SKILL.md](skill/SKILL.md) | Main skill documentation | 30 min |

### Reference Guides (Deep Dives)
- [Environment Management](skill/references/entity-management.md) — Creating entities, forms, tables
- [Solution Deployment](skill/references/solution-deployment.md) — Version tracking, sanitization, workflow
- [Security & Roles](skill/references/security-roles.md) — Teams, permissions, custom roles
- [Data Operations](skill/references/data-operations.md) — CSV/XML import, validation, deduplication
- [Integrations](skill/references/integrations.md) — SharePoint, Power Automate, workflows
- [D365 FO Development](skill/references/d365-fo-development.md) — X++ code review, testing, patterns

---

## 🔧 System Requirements

- **Python** 3.8+ (optional, for utilities)
- **Claude API** access (for using the skill)
- **Text Editor** (any editor works - VS Code, Sublime, etc.)

---

## 📋 Installation Methods

### Method 1: Automated (Recommended)
```bash
python scripts/install.py
```
- ✅ Checks Python version
- ✅ Creates directory structure
- ✅ Copies all files
- ✅ Generates preferences
- ✅ Validates installation

### Method 2: Manual
```bash
mkdir -p ~/.claude-skills/power-platform/skill/references
cp -r skill/* ~/.claude-skills/power-platform/skill/
cp QUICK_REFERENCE.md ~/.claude-skills/power-platform/
```

### Method 3: Docker
```bash
docker build -t power-platform-skill .
docker run -v ~/.claude-skills:/skills power-platform-skill
```

### Method 4: Development
```bash
python -m venv venv
source venv/bin/activate
pip install -r requirements-dev.txt
```

See [INSTALLATION.md](docs/INSTALLATION.md) for complete details on all methods.

---

## 📊 Workflow Overview

### How Different Users Get Help

```
┌─────────────────────────────────────────────────────────────┐
│              ROLE-BASED GUIDANCE PATHS                      │
└─────────────────────────────────────────────────────────────┘

SYSTEM ADMIN
  ↓
  ✓ Full access to all workflows
  ✓ No approvals needed for Dev/Test
  ✓ Approvals needed for PreProd/Prod
  ✓ Gets full deployment checklist
  ↓
  RESULT: Deploy with confidence

POWER PLATFORM MANAGER
  ↓
  ✓ Solution deployment workflows
  ✓ Security role management (team-level)
  ✓ Approval workflows included
  ✓ Team management guidance
  ↓
  RESULT: Manage team securely

D365 FO DEVELOPER
  ↓
  ✓ Code review guidance
  ✓ X++ patterns and best practices
  ✓ Testing strategies
  ✓ Integration patterns
  ↓
  RESULT: Develop confidently

CONFUSED USER
  ↓
  ✓ START_HERE.txt orientation
  ✓ Quick reference lookup
  ✓ Choose your path options
  ✓ Clear signposting
  ↓
  RESULT: Get oriented in 5-15 min
```

---

## 🎓 What You'll Learn

By using this skill, you'll understand:

✓ How to structure and manage Power Platform environments  
✓ The complete solution deployment lifecycle  
✓ How to implement security roles correctly (teams, not individuals)  
✓ Data import/export best practices  
✓ How to set up integrations (SharePoint, Power Automate, etc.)  
✓ D365 FO development patterns and best practices  
✓ Pre-deployment validation and risk mitigation  
✓ Troubleshooting common issues  
✓ Creating reusable templates and processes  

---

## 💡 Real-World Examples

### Example 1: Solution Deployment
```
Admin asks: "How do I deploy to production?"

Skill provides:
  1. Sanitize environment checklist
  2. Version number increment guidance
  3. 7-step deployment workflow
  4. Pre-deployment checklist
  5. Rollback procedures
  6. Post-deployment validation
  7. Documentation requirements
```

### Example 2: Security Role Setup
```
Manager asks: "How do I set up roles for my team?"

Skill provides:
  ✓ Critical rule: Never assign to individuals
  ✓ Team-based setup guide
  ✓ Permission depth explanations
  ✓ Custom role template
  ✓ Troubleshooting guide
  ✓ Approval workflow
  ✓ Documentation template
```

### Example 3: Code Review
```
Developer asks: "Review my X++ code?"

Skill provides:
  ✓ Structured review checklist
  ✓ Extension vs overlayering check
  ✓ Performance analysis
  ✓ Security concern validation
  ✓ TTS boundary check
  ✓ Error handling review
  ✓ Test scenario suggestions
```

---

## ⚙️ Configuration

### Preferences File
The skill stores your preferences in `preferences.yaml`:

```yaml
organization: "Acme Corp"
version_format: "1.0.YYYYMM"  # or MAJOR.MINOR.PATCH
user_role: "Admin"
environments:
  - name: "Dev"
    type: "Sandbox"
  - name: "Test"
    type: "Sandbox"
  - name: "PreProd"
    type: "Sandbox"
  - name: "Prod"
    type: "Production"
```

Generate preferences:
```bash
python scripts/generate-preferences.py
```

---

## 🤝 Contributing

We welcome contributions! See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

### How to Contribute
1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly
5. Submit a pull request

### Improvement Ideas
- Additional D365 FO patterns
- More integration scenarios
- Translated versions
- Video tutorials
- Community examples

---

## 📝 License

This project is licensed under the MIT License - see [LICENSE](LICENSE) file for details.

---

## 🆘 Support

### Getting Help
1. **Read** → Start with [QUICK_START.md](docs/QUICK_START.md)
2. **Search** → Check [FAQ.md](docs/FAQ.md)
3. **Explore** → Browse [skill/SKILL.md](skill/SKILL.md)
4. **Issues** → Open a GitHub issue for bugs
5. **Discussions** → Join discussions for questions

### Common Entry Points
- **Confused?** → [START_HERE.txt](START_HERE.txt)
- **Need quick answer?** → [QUICK_REFERENCE.md](QUICK_REFERENCE.md)
- **Want overview?** → [README.md](README.md)
- **Need detailed guide?** → [skill/SKILL.md](skill/SKILL.md)
- **Looking for template?** → [examples/](examples/) folder

---

## 📊 Documentation Statistics

- **Total Documentation:** 6,454+ lines
- **Files:** 12 markdown files + Python utilities
- **Topics Covered:** 50+ major workflows
- **Examples:** 100+ code samples and templates
- **Troubleshooting Guides:** 30+ common issues
- **Installation Methods:** 4 different approaches
- **Supported Platforms:** Windows, macOS, Linux
- **Python Version:** 3.8+

---

## 🎯 Roadmap

- [ ] Version 1.1 — Additional D365 CE customization patterns
- [ ] Version 1.2 — Power Automate workflow templates
- [ ] Version 1.3 — Integration scenario expansions
- [ ] Version 2.0 — Interactive CLI tool
- [ ] Translated versions — Spanish, French, German, Japanese

---

## 📚 Resources

- [Microsoft Dynamics 365 Docs](https://docs.microsoft.com/en-us/dynamics365/)
- [Power Platform Admin Center](https://admin.powerplatform.microsoft.com/)
- [Anthropic Claude Documentation](https://docs.anthropic.com/)

---

## 🙏 Acknowledgments

Built with care for the Dynamics 365 and Power Platform community.

Special thanks to all users who provided feedback and improvements!

---

## 📞 Contact

- **Issues & Bugs** — [GitHub Issues](https://github.com/yourusername/power-platform-skill/issues)
- **Discussions** — [GitHub Discussions](https://github.com/yourusername/power-platform-skill/discussions)
- **Email** — [contact@example.com](mailto:contact@example.com)

---

## ✨ Quick Links

- [Installation Guide](docs/INSTALLATION.md) — How to install
- [Quick Start](docs/QUICK_START.md) — Get started in 5 min
- [Main Skill](skill/SKILL.md) — Complete documentation
- [Quick Reference](QUICK_REFERENCE.md) — One-page cheat sheet
- [Visual Guides](docs/SKILL_VISUAL_GUIDE.md) — How it works (with diagrams)
- [FAQ](docs/FAQ.md) — Common questions
- [Contributing](CONTRIBUTING.md) — How to help

---

<div align="center">

**Ready to get started?** → [Start Here](START_HERE.txt)

**Want a visual explanation?** → [Visual Guide](docs/SKILL_VISUAL_GUIDE.md)

**Need help installing?** → [Installation Guide](docs/INSTALLATION.md)

Built with ❤️ for the Dynamics 365 community

</div>
