# Quick Reference Card - Power Platform & D365 Management Skill

## 📋 One-Page Cheat Sheet

### When to Use This Skill

✅ **Environment Management**
- Creating new Power Platform environments
- Configuring user access and licensing
- Managing environment settings

✅ **Solution Deployment**
- Deploying solutions Dev → Test → PreProd → Prod
- Tracking solution versions
- Rollback procedures

✅ **Security & Permissions**
- Creating security roles
- Managing teams and business units
- Fixing access issues

✅ **Data Operations**
- Importing CSV or XML files
- Validating data quality
- Deduplicating records

✅ **Integrations**
- Setting up SharePoint sync
- Configuring qualification notifications
- Connecting external systems

✅ **D365 FO Development**
- Generating X++ code
- Code review and validation
- Testing strategies

---

## 🚀 Quick Start

### Step 1: Clarify Your Role
- Dynamics Admin/Developer → Full access, no approvals
- Power Platform Manager → Solutions + security mgmt
- Team Lead → Team-level permissions
- Developer → X++ customizations
- Other → Specify your access level

### Step 2: State Your Goal
Examples:
- "I need to deploy a solution to Test"
- "Create a new security role"
- "Import customer data from CSV"
- "Review X++ code for performance"

### Step 3: Follow the Workflow
Skill provides step-by-step guidance + checklists + templates

---

## 📁 File Organization

| File | Purpose | When to Use |
|------|---------|------------|
| **SKILL.md** | Overview & main workflows | Starting point for any task |
| **d365-fo-development.md** | Claude Code for D365 FO | X++ code generation/review |
| **data-operations.md** | Import & validation | CSV/XML import workflows |
| **entity-management.md** | Entity & form design | Creating new entities/forms |
| **integrations.md** | SharePoint & qualifications | Setting up integrations |
| **security-roles.md** | Teams, BUs, permissions | Managing access & roles |

---

## 🔄 Core Workflows at a Glance

### Solution Deployment
```
Export from Dev (version++) 
  → Deploy to Test (validate)
  → Deploy to PreProd (validate)
  → Deploy to Prod (approval required)
  → Verify + Document
```

### Security Role Creation
```
Define purpose → Map entities & privileges 
  → Create role → Assign to Team (not individual)
  → Test with sample user → Document
```

### Data Import
```
Prepare CSV/XML → Map fields → Validate data
  → Review errors → Preview outcome → Import
```

### D365 FO Development
```
Draft requirements → Claude generates code
  → Implement → Claude reviews → Peer review
  → CI/CD gates → Merge → Deploy
```

---

## ⚠️ Critical Rules

### Security
- ❌ **NEVER** assign roles to individual users
- ✅ **ALWAYS** use Teams or Business Units
- ✅ Document team purpose and scope
- ✅ Audit access regularly

### Development
- ❌ No overlayering (use extensions only)
- ✅ Use Chain of Customization (CoC) patterns
- ✅ Test-driven development
- ✅ Automated quality gates

### Deployment
- ✅ Always sanitize environment first
- ✅ Maintain local solution backups
- ✅ Keep version numbers consistent
- ✅ Test rollback procedures

---

## 📊 Approval Requirements

| Task | Admin | Manager | Team Lead |
|------|-------|---------|-----------|
| Deploy to Prod | ❌ | ✅ | ✅ |
| Deploy to PreProd | ❌ | ❌ | ❌ |
| Create environment | ❌ | ✅ | ❌ |
| Change security role | ❌ | ❌ | ✅ |

---

## 🛠️ Common Templates

### Approval Request Template
```
Solution Name: ___________
Version Number: ___________
Target Environment: ___________
Solution Type: Managed / Unmanaged
Plugins: List any plugins
Connectors: List any connectors
Description: What does this change?
Impact: Any downtime? Restart required?
```

### Code Review Checklist
```
□ Extension vs. overlayering correct?
□ No N+1 query patterns?
□ Security risks identified?
□ TTS boundaries correct?
□ Error handling complete?
□ Unit tests written?
```

### Pre-Deployment Checklist
```
□ Solution exported and backed up
□ Version number follows format
□ Environment sanitized
□ All plugins listed
□ Approval obtained (if required)
□ Rollback plan confirmed
□ Post-deploy validation plan ready
```

---

## 🔍 Troubleshooting Quick Links

| Issue | Reference |
|-------|-----------|
| User can't see records | security-roles.md → Troubleshooting |
| Import fails | data-operations.md → Common Errors |
| SharePoint not syncing | integrations.md → Troubleshooting |
| Code won't compile | d365-fo-development.md → Root Cause |
| Form doesn't render | entity-management.md → Forms |

---

## 💾 Version Number Formats

**Ask the skill:** "What's your version format?"

Common examples:
- `1.0.YYYYMM` → 1.0.202403 (date-based)
- `MAJOR.MINOR.PATCH` → 2.1.3 (semantic)
- Sequential → 1.0, 1.1, 1.2
- Custom → Specify your format

The skill will remember your format for the session.

---

## 📞 Getting Help

### Within the Skill
- Ask clarifying questions anytime
- Request examples or templates
- Ask for troubleshooting help
- Request detailed explanations

### When Reporting Issues
Provide:
- Your role (Admin, Developer, Manager, etc.)
- What you're trying to do
- Error message (if any)
- Recent changes or context
- Environment name/type

### Using Browser Extension
- Share Power Platform UI screenshots
- Paste error messages and stack traces
- Copy code for review
- Share configuration details

---

## 🎯 Pro Tips

1. **Test in Dev First**
   - Always validate changes in Dev environment first
   - Never deploy directly to Prod

2. **Document Everything**
   - Keep notes on all configurations
   - Document team purposes
   - Record versioning decisions

3. **Use Templates**
   - Ask skill for templates
   - Reuse for consistency
   - Reduces errors

4. **Store Preferences**
   - Tell skill your version format once
   - Mention your role once
   - It remembers throughout session

5. **Leverage Code Review**
   - Always use Claude to review code
   - Before peer review
   - Catches 70% of issues

6. **Automate Quality Gates**
   - Set up CI/CD checks
   - Prevent bad code from merging
   - Saves time in testing

---

## 📚 Full Documentation

For comprehensive guidance, see:
- **README.md** — Getting started guide
- **SKILL.md** — All main workflows
- **Reference docs** — Deep dives by topic

---

## ✅ Checklist: First Time Using the Skill

- [ ] Read README.md
- [ ] Clarify your role with the skill
- [ ] Tell skill your version number format
- [ ] Ask for template for your first task
- [ ] Follow step-by-step guidance
- [ ] Use provided checklists
- [ ] Ask for clarification anytime
- [ ] Store preferences for next time

---

## Quick Links

```
SKILL.md → Start here for any task
d365-fo-development.md → For X++ or code review
data-operations.md → For data import/export
entity-management.md → For creating entities/forms
integrations.md → For SharePoint or notifications
security-roles.md → For access/permission issues
```

---

**Need help?** Ask the skill! It's designed to be helpful, practical, and adaptive to your needs.

