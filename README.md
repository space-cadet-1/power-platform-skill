# Power Platform & Dynamics 365 Management Skill

A comprehensive Claude skill for managing Microsoft Dynamics 365 and Power Platform environments, from environment setup through solution deployment, security management, data operations, integrations, and D365 FO development acceleration.

## Skill Overview

This skill provides expert guidance on:

### 📊 **Environment Management**
- Creating and configuring Power Platform environments
- Managing user access and licensing
- Environment isolation and data residency
- Setting up Dynamics 365 apps and features

### 🚀 **Solution Deployment**
- Version number tracking and management
- Deployment workflows (Dev → Test → PreProd → Prod)
- Approval processes and governance
- Rollback procedures and disaster recovery
- Solution sanitization best practices

### 🔐 **Security & Permissions**
- Team and Business Unit management
- Custom security role creation
- Permission depth levels (User, BU, Parent/Child, Organization)
- Segregation of Duties (SoD) compliance
- Access control auditing

### 📁 **Data Operations**
- CSV import workflows with validation
- XML schema mapping
- Data deduplication and conflict resolution
- Import error troubleshooting
- Data quality checks

### 🔗 **Integrations**
- SharePoint document library sync
- Qualification expiration tracking
- Automated notification workflows
- Power Platform, OData, and Azure integrations
- Dual-write setup and conflict resolution

### 💻 **D365 FO Development**
- Claude Code workflows for X++ development
- Code generation with prompt templates
- Structured code review checklists
- Testing strategies and edge case handling
- CI/CD pipeline setup and automated quality gates
- Extension patterns (Chain of Customization)
- Integration development (OData, dual-write, Azure)

## Skill Structure

```
power-platform-management/
├── SKILL.md                          # Main skill file (entry point)
└── references/
    ├── d365-fo-development.md        # Claude Code & D365 FO development
    ├── data-operations.md             # CSV/XML import, validation, deduplication
    ├── entity-management.md           # Entity creation, forms, relationships
    ├── integrations.md                # SharePoint, qualifications, workflows
    └── security-roles.md              # Roles, teams, BUs, permissions
```

## Key Features

✅ **Role-Based Guidance** — Adapts to your role (Admin, Manager, Developer, Power User)
✅ **Persistent Preferences** — Remembers your versioning format, naming conventions, role scope
✅ **Comprehensive Workflows** — Step-by-step guidance for every major task
✅ **Real-World Examples** — Practical scenarios, templates, and decision trees
✅ **Troubleshooting Guides** — Common issues and solutions for every topic
✅ **Pre-Deployment Checklists** — Environment-specific and role-based validation
✅ **Development Acceleration** — Claude Code prompts and code review templates
✅ **Browser-Extension Friendly** — Guides users through UI without backend integration

## Getting Started

### 1. **Identify Your Role**
Start by clarifying your role in Dynamics 365/Power Platform:
- Dynamics Admin/Developer (full access, no approvals)
- Power Platform Manager (solution deployment, team management)
- Team Lead (team-level permissions, limited deployments)
- Power User (forms, basic customizations)
- Custom Role (specify your access level)

### 2. **State Your Goal**
Tell the skill what you're trying to accomplish:
- "I need to create a new environment"
- "I need to deploy a solution from Dev to Test"
- "I need to set up SharePoint document integration"
- "I need to review X++ code for a D365 FO customization"
- "I need to create a new security role"

### 3. **Follow the Guidance**
The skill will:
- Ask clarifying questions about your setup
- Provide step-by-step workflows
- Share checklists and templates
- Offer troubleshooting when issues arise
- Store your preferences for future sessions

## When to Use This Skill

Use this skill whenever you:
- Create or manage Power Platform environments
- Deploy solutions between environments
- Manage security roles and permissions
- Import or export data
- Set up integrations (SharePoint, qualifications, etc.)
- Develop D365 FO solutions using X++ or integrations
- Perform pre-deployment validation
- Troubleshoot access or deployment issues
- Review code for quality and best practices

## Reference Documents

### Main SKILL.md
- **Purpose:** Overview, workflows, checklists
- **When to read:** Starting point for any task
- **Length:** ~500 lines
- **Content:** Quick navigation, role definitions, all major workflows

### d365-fo-development.md
- **Purpose:** Accelerate D365 FO development using Claude Code
- **When to read:** Generating X++ code, code review, testing
- **Length:** ~600 lines
- **Content:** Prompt templates, code review checklists, patterns, workflows

### data-operations.md
- **Purpose:** Data import, validation, deduplication
- **When to read:** Working with CSV/XML imports, data quality issues
- **Length:** ~450 lines
- **Content:** Step-by-step import workflows, error troubleshooting, deduplication strategies

### entity-management.md
- **Purpose:** Entity creation, form design, relationships
- **When to read:** Creating new entities or forms, managing relationships
- **Length:** ~400 lines
- **Content:** Entity design, form layout, relationship types, deployment

### integrations.md
- **Purpose:** SharePoint, qualifications, external system integration
- **When to read:** Setting up document sync or notification workflows
- **Length:** ~500 lines
- **Content:** Integration patterns, setup workflows, notification automation

### security-roles.md
- **Purpose:** Security role design and permission management
- **When to read:** Creating roles, managing teams/BUs, troubleshooting access
- **Length:** ~400 lines
- **Content:** Role creation, permission depth levels, team management, troubleshooting

## Common Workflows

### Deploying a Solution Across All Environments
1. Export from Dev with incremented version
2. Deploy to Test → Validate
3. Deploy to PreProd → Validate
4. Deploy to Prod with approval
5. Rollback plan in place

### Creating a New Security Role
1. Define role purpose and scope
2. Map required entities and privileges
3. Create role with appropriate depth levels
4. Assign to team (not individuals)
5. Test with sample user
6. Document for future reference

### Setting Up Qualification Expiration Notifications
1. Verify qualification storage (field or entity)
2. Define notification timing and recipients
3. Create Power Automate flow
4. Set up scheduled triggers
5. Test with sample data
6. Document maintenance plan

### Developing D365 FO Solution with Claude Code
1. Draft requirements and acceptance criteria
2. Generate code skeleton from Claude
3. Implement business logic
4. Use Claude for structured code review
5. Peer review via PR
6. Automated quality gates
7. Merge and deploy

## Best Practices

### Environment Management
- ✅ Always sanitize target environment before deployment
- ✅ Maintain local backups of solutions before upgrades
- ✅ Document all environment-specific configurations
- ✅ Use consistent naming conventions across all environments

### Security & Permissions
- ⚠️ **NEVER** assign roles to individual users
- ✅ Always use Teams or Business Units
- ✅ Document team purpose and role scope
- ✅ Regular audit of user access

### Data Operations
- ✅ Always test imports in Dev first
- ✅ Validate data quality before import
- ✅ Keep backup of source data
- ✅ Verify data after import

### D365 FO Development
- ✅ Use extensions only (no overlayering)
- ✅ Write tests before implementing
- ✅ Use Claude as first draft + reviewer
- ✅ Enforce automated quality gates
- ✅ Document edge cases explicitly

## Approval Workflow

The skill guides approval workflows based on your role:

| Task | Admin/Dev | Manager | Team Lead |
|------|-----------|---------|-----------|
| Deploy to Prod | No approval | Needs approval | Needs approval |
| Create environment | No approval | Needs approval | N/A |
| Change security role | No approval | Self-serve | Needs approval |
| Deploy to Test | No approval | No approval | No approval |

## Storage & Preferences

This skill stores and references your preferences throughout the session:

- **Version number format** (e.g., 1.0.YYYYMM, MAJOR.MINOR.PATCH)
- **User role** (Admin, Manager, Team Lead, etc.)
- **Naming conventions** (entities, fields, forms)
- **Environment structure** (Dev, Test, PreProd, Prod)
- **Team/BU structure** (for security role management)
- **Integration preferences** (SharePoint, Azure, etc.)

These preferences are used to provide consistent, tailored guidance throughout your interactions.

## Getting Help

### Within the Skill
- Ask clarifying questions anytime
- Request examples or templates
- Ask for troubleshooting help
- Request detailed explanations

### Reporting Issues
Provide:
- What you're trying to accomplish
- Your user role and environment
- Specific error messages or symptoms
- Recent changes or context
- Steps to reproduce (if applicable)

### Using the Browser Extension
The skill works seamlessly with Claude's browser extension:
- Read Power Platform UI pages
- Get guidance on specific screens
- Copy error messages and stack traces
- Share configuration details
- Paste code for review

## Advanced Topics

### CI/CD Pipeline Setup
See `d365-fo-development.md` → Workflow Automation (CI/CD)

### Dual-Write Integrations
See `d365-fo-development.md` → Integration Scenarios

### Advanced Security Scenarios
See `security-roles.md` → Troubleshooting

### Complex Data Migration
See `data-operations.md` → Data Deduplication

### Root Cause Analysis
See `d365-fo-development.md` → Root Cause Analysis Prompt Template

## Tips for Best Results

1. **Be Specific** — "I need to deploy a solution to PreProd" is better than "deploy"
2. **Provide Context** — Share your role, environment setup, constraints
3. **Ask for Templates** — Get reusable prompts, checklists, workflows
4. **Use the Browser Extension** — Share actual error messages and stack traces
5. **Store Preferences** — Tell the skill about your version format, naming conventions
6. **Reference Examples** — Ask for real-world scenarios similar to your need
7. **Test in Dev First** — Always validate in lower environments before Prod

## Skill Version & Updates

- **Version:** 1.0
- **Last Updated:** March 2026
- **Coverage:** Dynamics 365 CE & FO, Power Apps, Power Automate, Power Platform

---

## Questions?

If you have questions about:
- **Using this skill** → Ask within the chat
- **Specific topics** → Reference the appropriate guide above
- **Real-world scenarios** → Describe your situation and ask for guidance
- **Code review** → Share your code and specify what you want reviewed

The skill is designed to be helpful, practical, and adaptable to your specific needs.

