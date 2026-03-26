---
name: power-platform-management
description: |
  Comprehensive guide for managing Microsoft Dynamics 365 and Power Platform environments, plus D365 FO development acceleration. Use this skill whenever the user mentions: creating/managing Power Platform environments, deploying or pushing solutions between environments (Dev → Test → PreProd → Prod), managing security roles at team/business unit level, importing/exporting data or solutions, setting up integrations (SharePoint, qualification expiration triggers), performing environment maintenance tasks, OR developing D365 FO solutions using X++ customizations and integrations (OData, dual-write, Power Platform, Azure). The skill provides step-by-step workflows, pre-deployment checklists, approval preparation guidance, best practices for solution versioning, security governance, data operations, and code generation/review workflows using Claude Code. Always trigger when users work with Dynamics 365, Power Apps, Power Automate, Power Platform administration, or D365 FO development tasks.
compatibility: |
  - Microsoft Dynamics 365 / Power Platform access
  - Admin or Developer role within environments
  - Browser access to Power Platform admin center
---

# Dynamics 365 & Power Platform Management Skill

This skill provides comprehensive guidance for managing Microsoft Dynamics 365 and Power Platform environments at every level. It covers environment creation, solution deployment workflows, security role management, data operations, integrations, and pre-deployment validation.

## Quick Navigation

**Core Workflows:**
- [Environment Management](#environment-management)
- [Solution Deployment & Versioning](#solution-deployment--versioning)
- [Security & Permissions](#security--permissions)
- [Data Operations](#data-operations)
- [Integrations](#integrations)
- [D365 FO Development with Claude Code](#d365-fo-development-with-claude-code)
- [Pre-Deployment Checklist](#pre-deployment-checklist)

## User Roles & Access Levels

The skill adapts based on the user's role. **Ask the user to clarify their role at the start of the conversation** if it's not already clear:

| Role | Approval Required? | Can Deploy? | Can Manage Security? | Can Modify Entities? |
|------|-------------------|------------|----------------------|---------------------|
| **Dynamics Admin/Developer** | No | Yes, all envs | Yes | Yes |
| **Power Platform Manager** | Yes (for prod) | Yes (with approval) | Yes (business unit level) | Yes (with approval) |
| **Team Lead** | Yes (always) | Yes (with approval) | Yes (team level only) | Limited |
| **Power User** | Yes (always) | No | No | Limited |
| **Custom Role** | Depends | Ask user | Ask user | Ask user |

---

## Environment Management

### Creating Environments

**Prerequisites:**
- Admin or Developer role in Power Platform admin center
- Appropriate licensing in Microsoft Azure
- Understanding of environment isolation and data residency requirements

**Steps to Create an Environment:**

1. **Access Power Platform Admin Center**
   - Navigate to admin.powerplatform.microsoft.com
   - Select "Environments" from the left menu
   - Click "New environment"

2. **Configure Environment Settings**
   - **Name:** Use a naming convention (e.g., `CompanyName-Dev`, `CompanyName-Test`)
   - **Type:** Choose between Sandbox or Production
   - **Region:** Select appropriate region for data residency
   - **Database:** Create with or without sample data (recommended: without for dev)

3. **Enable Dynamics 365** (if applicable)
   - If using Dynamics 365, enable it during environment creation
   - Select default security role for users
   - Choose Dynamics 365 apps to install

4. **Manage User Access**
   - ⚠️ **IMPORTANT:** Assign users at **team/business unit level**, never individually
   - Use Azure AD groups for scalability
   - Verify licensing in Azure before granting access

5. **Document the Environment**
   - Record environment URL, purpose (Dev/Test/PreProd/Prod)
   - Store environment ID for API calls
   - Note any plugins or custom connectors needed

**Common Issues:**
- Licensing conflicts → Check Azure license management
- Region restrictions → Verify data residency requirements
- Connector access → Some connectors require additional licensing

---

## Solution Deployment & Versioning

### Version Number Tracking

**Before starting any deployment, confirm the versioning format:**

> "How does your organization track solution versions? For example:
> - Date-based: `1.0.YYYYMM` (e.g., 1.0.202403)
> - Semantic: `MAJOR.MINOR.PATCH` (e.g., 2.1.3)
> - Sequential: `1.0`, `1.1`, `1.2`
> - Other custom format?"

**Store this preference for the session.** Whenever versions are mentioned, use this format.

### Pre-Deployment Steps

**Environment Sanitization (CRITICAL):**
Before deploying to an environment, ensure it's clean:

1. Identify all solutions currently installed
2. Remove unnecessary solutions (keep only essentials)
3. Document what's being removed (for rollback)
4. Verify no active plugins or workflows depend on removed solutions
5. Clear temporary data or test records

**Why?** Minimal solutions = fewer conflicts, faster deployments, easier rollbacks.

### Solution Deployment Workflow

**Standard Path:** Dev → Test → PreProd → Prod

For each environment transition:

1. **Export Solution from Source Environment**
   - Go to Maker Studio (make.powerapps.com)
   - Select solution
   - Click "Export" → Choose "Managed" or "Unmanaged"
   - Microsoft Power Platform auto-increments version number (you can increase it further, but never decrease)
   - Download .zip file
   - **Create a local backup of this file immediately**

2. **Prepare Approval Request** (unless user is Dynamics Admin with no approval required)
   - Solution name
   - Current version number
   - Target environment
   - Solution type: Managed or Unmanaged?
   - List of plugins included (if any)
   - List of connectors/dependencies
   - Brief description of changes (e.g., "Bug fixes for customer portal", "New entity: ServiceRequest")
   - Expected impact (e.g., "No downtime", "5-minute restart required")

3. **Obtain Approval** (if required based on role)
   - Present the prepared information to appropriate approver
   - Approver confirms: solution changes, version alignment, plugins, connectors
   - Approver clicks approval (document this confirmation)

4. **Import Solution to Target Environment**
   - Go to target environment → Maker Studio
   - Click "Import solution"
   - Upload the .zip file
   - Review import configuration (preserve customizations, etc.)
   - Click "Import"
   - Wait for import to complete and verify success

5. **Post-Deployment Validation**
   - ✅ Forms render correctly
   - ✅ Workflows trigger properly
   - ✅ Plugins execute without errors
   - ✅ Connections/connectors authenticate
   - ✅ No data corruption occurred

6. **Document Deployment**
   - Record deployment date/time
   - Version number in target environment
   - Any issues encountered
   - Approver name (if applicable)

### Rollback Procedures

**If a deployment causes problems:**

1. **Assess Impact**
   - Is the environment unusable?
   - Are specific features broken?
   - Is data corruption occurring?

2. **Execute Rollback**
   - Go to target environment → Solutions
   - Select the problematic solution
   - Click "Delete" or "Uninstall"
   - Import the previous solution version (from your local backup)
   - Verify functionality is restored

3. **Post-Rollback Analysis**
   - What caused the issue?
   - Document the root cause
   - Determine if solution needs modification before re-deployment
   - Consider adding to pre-deployment checklist

**Prevention:**
Always maintain a local backup of the previous solution version before deploying new versions.

---

## Security & Permissions

### ⚠️ Critical Rule: No Individual User Access

**Never assign security roles or environment access to individual users.** Always use:
- **Team-level assignments** (smaller, tactical groups)
- **Business Unit assignments** (larger, organizational structure)

### Managing Team & Business Unit Access

**1. Creating/Modifying Teams**
- Go to environment → Settings → Security → Teams
- Define team membership and purpose
- Assign appropriate security role to team
- Never assign multiple different roles to a team

**2. Custom Security Roles**
- Go to Settings → Security → Security Roles
- Click "New" to create custom role
- Define privileges by entity:
  - Create, Read, Update, Delete (CRUD)
  - Share, Assign, Append, Append To
- Set privilege depth: User, Business Unit, Parent/Child BU, Organization
- Assign role to team or business unit (not individuals)

**3. Business Unit Hierarchy**
- Structure reflects organizational needs
- Security roles inherit down the hierarchy
- Parent business unit has visibility over child business units (configurable)
- Document your BU structure before assigning roles

### Typical Role Examples

**Example 1: Customer Service Team**
- Team: "Customer Service - North Region"
- Business Unit: "Customer Service"
- Security Role: "Customer Service Rep"
- Privileges: Read/Update Contacts & Cases, limited Account access

**Example 2: Development Team**
- Team: "Dynamics Developers"
- Business Unit: "IT"
- Security Role: "Solution Developer" (custom role with broader privileges)
- Privileges: Full CRUD on all entities, plugin registration, customizations

**Important:** If user authorization changes or team membership changes, update at the team/BU level, not at individual level.

---

## Data Operations

See **[references/data-operations.md](references/data-operations.md)** for detailed guidance on:
- CSV import workflows
- XML schema mapping and validation
- Data deduplication and error resolution
- Import visualization and preview
- Common import errors and troubleshooting

### Quick Reference: CSV Import

1. Prepare CSV file with proper headers matching entity columns
2. Go to environment → Data → Import
3. Upload CSV file
4. Map columns to entity fields
5. Review validation results (data quality check happens here)
6. Preview outcome before final import
7. Execute import and verify record count

### Quick Reference: XML Mapping

1. Verify schema exists in target environment (if not, import schema first)
2. Go to Data → Import → XML mapping
3. Load XML file
4. Verify against existing schema
5. Review transformation preview
6. ⚠️ If schema doesn't exist → error will occur, must import schema first
7. Execute mapping

---

## Integrations

See **[references/integrations.md](references/integrations.md)** for detailed guidance on:
- SharePoint document library integration
- Qualification expiration triggers and notifications
- Setting up automated reminder workflows
- Best practices for CRM-SharePoint synchronization

### Quick Reference: SharePoint Integration

**Ask user to clarify:**
- Embedding SharePoint documents in CRM records, or syncing library?
- Required folder structure/naming conventions?

**Basic Setup:**
1. Create SharePoint site/library
2. In Power Platform → Environments → Features → SharePoint
3. Configure site mapping to CRM entities
4. Test document creation/sync

### Quick Reference: Qualification Expiration

**User specifies:**
- Custom field or record for storing qualifications
- Expiration date field
- Notification timing (e.g., 30 days before expiration)
- Who gets notified (CRM Manager, qualification holder, both)

**Setup:**
1. Create custom field for expiration date (Date type)
2. Create Power Automate flow triggered daily
3. Flow logic: Find records expiring within X days
4. Send email notifications
5. Document the flow for future updates

---

## D365 FO Development with Claude Code

See **[references/d365-fo-development.md](references/d365-fo-development.md)** for detailed guidance on:
- Using Claude Code to accelerate D365 FO development
- Code generation and review workflows
- X++ customization patterns (extensions, CoC)
- Integration development (OData, dual-write, Power Platform, Azure)
- Testing strategies and automated quality gates
- CI/CD pipeline setup and validation

### Quick Summary

**The High-Impact Workflow:**

```
Developer Drafts Requirements
    ↓
Claude Generates First-Pass Code + Edge Cases
    ↓
Developer Implements & Compiles
    ↓
Claude Performs Structured Review (Security, Performance, TTS)
    ↓
Peer Review via PR
    ↓
Automated Checks (CI: Compile, Tests, Static Analysis)
    ↓
Merge → Deploy → Smoke Tests
```

**Key Principles:**
- ✅ Treat Claude as "first draft + reviewer", not replacement for developers
- ✅ Use standardized prompt templates for consistency
- ✅ Enforce extension-only development (no overlayering)
- ✅ Add automated quality gates (compile, tests, security scan)
- ✅ Review for: Extension correctness, Performance, Security, TTS boundaries, Error handling
- ✅ Document edge cases explicitly in requirements

**When to Use:**
- X++ customizations (forms, classes, entities)
- Integration development (OData, Power Platform, Azure)
- Code review and quality validation
- Test case generation
- Root cause analysis on failures

---

## Pre-Deployment Checklist

**Before deploying ANY solution, review this checklist based on your role:**

### For All Roles:

- [ ] Solution has been exported and backed up locally
- [ ] Version number follows our format: ________ (e.g., 1.0.202403)
- [ ] Target environment has been sanitized (unnecessary solutions removed)
- [ ] All plugins are documented and listed
- [ ] All connectors/dependencies are documented
- [ ] Change description prepared (what is this solution doing?)
- [ ] Expected impact defined (downtime? restart required?)

### For Non-Admin Roles (requires approval):

- [ ] Approval request prepared with all above information
- [ ] Appropriate approver identified
- [ ] Approval obtained and documented
- [ ] Approver confirmed solution changes, version, plugins, connectors

### For Admin Roles:

- [ ] Team/stakeholders notified of deployment window (if applicable)
- [ ] Rollback plan confirmed (previous version backed up)
- [ ] Post-deployment validation plan identified (who tests what?)

### Environment-Specific Checks:

**Dev Environment:**
- [ ] Can proceed immediately, minimal validation needed

**Test Environment:**
- [ ] User acceptance testing (UAT) window scheduled
- [ ] Test cases prepared
- [ ] Known issues documented

**PreProd Environment:**
- [ ] Data matches production (realistic volume)
- [ ] Performance tested
- [ ] All integrations verified
- [ ] Approval from business owner obtained

**Prod Environment:**
- [ ] Maintenance window scheduled (if required)
- [ ] Stakeholders notified
- [ ] Production data backup taken
- [ ] Monitoring/alerting configured
- [ ] Final approval from Product Owner or CTO obtained

---

## Common Workflows

### Deploying a Bug Fix Across All Environments

1. Fix bug in Dev environment
2. Export solution with incremented version (e.g., 1.0.202403 → 1.0.202404)
3. Create local backup
4. Deploy to Test → validate → approve if needed
5. Deploy to PreProd → validate → approve if needed
6. Deploy to Prod → validate → notify stakeholders

### Creating a New Entity and Deploying It

1. Create entity in Dev environment (fields, relationships, forms, views)
2. Test in Dev (create test records, verify forms/workflows)
3. Export solution with new entity (version increment)
4. Deploy to Test → user acceptance testing
5. Deploy to PreProd → performance testing
6. Deploy to Prod → monitor performance

### Adding a Team and Assigning Permissions

1. Go to environment → Settings → Security → Teams
2. Click "New" and create team
3. Add team members (from Azure AD group preferred)
4. Assign security role to team (never to individuals)
5. Verify team members have appropriate access
6. Document team purpose and role assignment

### Setting Up Qualification Expiration Notifications

1. Verify custom field exists for expiration date
2. Create Power Automate flow
3. Flow trigger: Scheduled (daily) or Recurrence
4. Flow action: Get records expiring within X days
5. Flow action: Send email to CRM Manager + Qualification Holder
6. Test with sample data
7. Document flow location and maintenance notes

---

## When to Consult Reference Documents

- **D365 FO development with Claude Code** → See `references/d365-fo-development.md`
- **Data import/export issues** → See `references/data-operations.md`
- **SharePoint or qualification setup** → See `references/integrations.md`
- **Security role design** → See `references/security-roles.md`
- **Entity/form creation best practices** → See `references/entity-management.md`
- **Deployment troubleshooting** → See `references/solution-deployment.md`

---

## Storage & Preferences

This skill stores user preferences to provide consistent guidance:

**Preferences stored this session:**
- User role and access level
- Organization's version number format
- Environment naming conventions (if any)
- Custom naming conventions for forms/entities (if any)
- SharePoint integration folder structure (if applicable)
- Approval workflow requirements

These will be referenced throughout the session to provide tailored guidance.

---

## Getting Help

If you encounter an issue not covered here:
1. **Clearly describe** the problem, error message, and what you're trying to accomplish
2. **Provide context** — which environment, which solution, which step in the process
3. **Share relevant details** — version numbers, plugins, connectors, user roles involved
4. I'll help you troubleshoot and document the solution for future reference

