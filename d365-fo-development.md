# Claude Code & D365 FO Development Workflow

This document provides guidance on using Claude Code to accelerate Dynamics 365 Finance & Operations (D365 FO) development while maintaining quality and reducing errors.

## Table of Contents

1. [Overview & Key Principles](#overview--key-principles)
2. [Development Workflow](#development-workflow)
3. [Prompt Templates](#prompt-templates)
4. [Code Review Checklists](#code-review-checklists)
5. [Testing Strategy](#testing-strategy)
6. [Common Patterns](#common-patterns)
7. [Best Practices](#best-practices)

---

## Overview & Key Principles

### Goal

Accelerate D365 FO development cycles while reducing human error through standardized processes, AI-assisted code generation and review, and automated quality gates.

### Core Philosophy

**Treat Claude as a standardized "first draft + reviewer"** — not a replacement for developers, but a force multiplier that:
- Generates consistent code skeletons
- Catches common mistakes early
- Enforces best practices
- Reduces review cycles
- Accelerates pair programming

### Key Takeaways

✅ **This is absolutely doable** — Claude can effectively assist D365 FO development
✅ **Best results require guardrails** — Standardized prompts, templates, and gates matter
✅ **High ROI areas:**
- X++ customizations (forms, classes, entities)
- Integrations (OData, dual-write, Power Platform, Azure)
- Code review and quality gates
- Test case generation

---

## Development Workflow

### The High-Impact Cycle

This workflow consistently produces better outcomes with less rework:

```
1. Developer Drafts Requirements
   ↓
2. AI Generates First-Pass Code + Edge Cases
   ↓
3. Developer Implements & Compiles
   ↓
4. AI Performs Structured Review
   ↓
5. Peer Review via PR
   ↓
6. CI Build + Automated Checks
   ↓
7. Merge → Deploy → Smoke Tests
```

### Step-by-Step Execution

**Step 1: Draft Requirements**

Developer creates (or AI helps draft):
- **Feature Summary:** What are we building?
- **Acceptance Criteria:** What makes this "done"?
- **Constraints:** Any technical limitations?
- **Edge Cases:** What could go wrong?

**Example:**

```
FEATURE: Create new expense report approval form

SUMMARY:
Expense reports over $5,000 require manager approval 
before submission. Create a new form to display approval status.

ACCEPTANCE CRITERIA:
✓ Form displays approval status (Pending, Approved, Rejected)
✓ Manager can approve/reject with comment
✓ Notification sent when status changes
✓ Form integrates with existing Expense Report entity
✓ Mobile-friendly

CONSTRAINTS:
- Use extensions only (no overlayering)
- Performance: < 2 second load time
- Support multiple currencies
- Comply with Segregation of Duties (SoD)

EDGE CASES:
- What if manager is also the expense submitter? (conflict)
- What if expense is modified after approval request? (re-route)
- What if manager is deleted? (reassign approval)
- Concurrent approvals from multiple managers? (first wins)
```

**Step 2: AI Generates First-Pass Code**

Use Claude with standardized prompt (see [Prompt Templates](#prompt-templates) below).

Claude generates:
- X++ code skeleton following best practices
- Comments explaining non-obvious logic
- Edge case handling
- Test scenarios to consider

**What you get:**
- Consistent structure
- CoC (Chain of Customization) patterns
- Error handling stubs
- Performance considerations called out

**Step 3: Developer Implements**

Developer takes the skeleton and:
- Fills in business logic details
- Implements actual approval workflow
- Adds data validation
- Tests locally in sandbox
- Compiles with zero warnings

**Step 4: AI Performs Structured Review**

Use Claude's code review prompt to validate:
- ✅ Extension vs. overlayering approach correct?
- ✅ Performance risks? (query loops, batch size, etc.)
- ✅ Security assumptions? (SoD, privilege escalation risks)
- ✅ Transaction boundaries (TTS) correct?
- ✅ Error handling complete?
- ✅ Test coverage adequate?

Claude provides:
- Specific improvement suggestions
- Security/performance concerns
- Required test scenarios
- Definition of Done checklist

**Step 5: Peer Review**

Standard PR process with focus on:
- Business logic correctness
- Alignment with requirements
- Code quality improvements
- Documentation

**Step 6: Automated Gates (CI/CD)**

Before merge, enforce:
- [ ] Code compiles with zero errors/warnings
- [ ] Static analysis passes (best practice rules)
- [ ] Unit tests pass
- [ ] Code coverage meets threshold (>80%)
- [ ] PR template completed
- [ ] No overlayering detected

**Step 7: Deploy & Smoke Tests**

- Merge to main branch
- Deploy to test environment
- Run smoke tests
- Monitor for errors

---

## Prompt Templates

### Template 1: Generate X++ Code

**Use this when:** You need Claude to generate a first-pass code skeleton

```
You are a Dynamics 365 Finance & Operations (D365 FO) developer.

TASK: Write X++ code for the following feature.

FEATURE REQUIREMENTS:
[Copy feature summary, acceptance criteria, constraints from Step 1]

IMPLEMENTATION GUIDELINES:
- Use EXTENSIONS ONLY (no overlayering) — use Chain of Customization (CoC) patterns
- Follow X++ best practices and D365 FO coding standards
- Assume the base functionality exists; only extend/override as needed
- Include meaningful comments explaining non-obvious logic
- Handle errors gracefully (try/catch, error logging)
- Consider performance implications (avoid N+1 queries, use batch operations)
- Validate all inputs and data

DELIVERABLES:
1. Complete X++ code with comments
2. List of edge cases identified and handled
3. Required test scenarios (unit tests to write)
4. Known limitations or potential improvements
5. Any external dependencies or configurations needed

ACCEPTANCE CRITERIA:
[List from requirements]

CODE CONSTRAINTS:
[List from requirements]

Please provide the code, along with explanations for any design decisions.
```

**Expected output:**
- Compilable X++ code
- Edge case handling
- Test scenarios
- Comments explaining logic

### Template 2: Review X++ Code

**Use this when:** You want Claude to review code for quality, security, and best practices

```
You are a D365 FO code reviewer performing a quality gate check.

REVIEW THIS CODE:
[Paste X++ code to review]

CONTEXT:
- Feature: [Brief feature description]
- File: [Filename]
- Type: [Form, Class, Entity customization, etc.]
- Dependencies: [Any relevant context]

REVIEW CHECKLIST — Evaluate and comment on:

1. EXTENSION VS. OVERLAYERING
   - Is this using Chain of Customization correctly?
   - Are extends/override patterns appropriate?
   - Any overlayering detected?

2. PERFORMANCE
   - Any N+1 query patterns?
   - Large data operations without batching?
   - Unnecessary loops or nested queries?
   - Caching opportunities missed?
   - Suggest specific optimizations

3. SECURITY
   - Privilege escalation risks?
   - SQL injection risks?
   - Segregation of Duties (SoD) concerns?
   - Data access control appropriate?

4. TRANSACTION BOUNDARIES (TTS)
   - ttsBegin/ttsCommit used correctly?
   - Nested transactions handled?
   - Rollback on error?

5. ERROR HANDLING
   - All exceptions caught?
   - User-friendly error messages?
   - Logging in place?
   - Rethrow vs. handle decisions correct?

6. CODE QUALITY
   - Variable naming clear?
   - Comments adequate?
   - Complexity reasonable?
   - Follows D365 naming conventions?

7. TESTING
   - Unit test cases identified?
   - Edge cases covered?
   - Test data strategy clear?

DELIVERABLES:
1. Summary: Pass / Needs Improvement
2. Critical issues (must fix before merge)
3. Important issues (should fix before merge)
4. Nice-to-have improvements
5. Specific test scenarios to validate
6. Definition of Done checklist for developer

Be specific and actionable. If you suggest changes, explain why.
```

**Expected output:**
- Pass/fail assessment
- Specific issues with line numbers
- Actionable improvement suggestions
- Test checklist

### Template 3: Root Cause Analysis

**Use this when:** Code is failing and you need to diagnose the problem

```
You are a D365 FO troubleshooter performing root cause analysis.

EXCEPTION INFORMATION:
Exception Type: [e.g., DuplicateKeyException, AccessViolationException]
Message: [Full exception message]
Call Stack:
[Paste call stack]

RELEVANT CODE:
[Paste the method/class where exception occurred]

CONTEXT:
- What was being executed when error occurred?
- Recent changes to this code?
- Frequency: Always happens? Intermittent?
- Reproduced steps: [How to trigger]
- Data volume: Normal or peak load?

ANALYSIS:
1. List the 5 most likely root causes
2. For each, explain why and how to verify
3. Most probable cause (with confidence level)
4. Immediate workaround (if any)
5. Permanent fix recommendation

NEXT STEPS:
1. Top 5 things to check first (specific, actionable)
2. Suggested debugging approach
3. Data to collect for deeper investigation
4. Preventive measures for future

Be specific. If you need more information to diagnose, ask for it.
```

**Expected output:**
- Ranked list of probable causes
- Diagnostic steps
- Fix recommendations
- Prevention strategies

---

## Code Review Checklists

### Pre-Commit Checklist (Developer)

Before submitting code for review, developer verifies:

**Code Quality:**
- [ ] Code compiles with zero errors
- [ ] Code compiles with zero warnings
- [ ] No overlayering (extends/override only)
- [ ] Naming conventions followed (camelCase, PascalCase)
- [ ] Comments added for complex logic
- [ ] No hardcoded values (use configuration)
- [ ] No commented-out code (clean up)

**Performance:**
- [ ] No N+1 query patterns
- [ ] Large data operations use batch processing
- [ ] Query select() lists specific fields (not *)
- [ ] Unnecessary loops eliminated
- [ ] Caching used where appropriate

**Security:**
- [ ] Input validation on all parameters
- [ ] No SQL injection risks (use X++ queries, not SQL strings)
- [ ] Appropriate privilege checks
- [ ] SoD principles maintained
- [ ] No hardcoded passwords/credentials

**Testing:**
- [ ] Unit tests written (>80% coverage)
- [ ] Unit tests pass locally
- [ ] Edge cases tested
- [ ] Error scenarios tested
- [ ] No test data left in code

**Documentation:**
- [ ] Method comments (purpose, parameters, return)
- [ ] Complex logic explained
- [ ] Edge cases documented
- [ ] Dependencies listed

### Peer Review Checklist

PR reviewer verifies:

**Requirements Alignment:**
- [ ] Code matches acceptance criteria
- [ ] Feature works as intended
- [ ] No scope creep
- [ ] Addresses all edge cases mentioned

**Code Review:**
- [ ] Follows team coding standards
- [ ] Performance appropriate
- [ ] Security concerns addressed
- [ ] Error handling complete
- [ ] Tests adequate

**Business Logic:**
- [ ] Business rules correctly implemented
- [ ] Data integrity maintained
- [ ] User experience appropriate
- [ ] Workflow integrations correct

**Approval:**
- [ ] Approved by tech lead or peer
- [ ] All feedback addressed
- [ ] Ready for merge

### Automated Gate Checklist (CI/CD)

These checks run automatically on every PR:

**Compilation:**
- [ ] Zero compilation errors
- [ ] Zero compilation warnings
- [ ] All dependencies resolved

**Code Analysis:**
- [ ] Static analysis passes (linting rules)
- [ ] No security vulnerabilities detected
- [ ] Performance metrics acceptable
- [ ] Code complexity within limits

**Testing:**
- [ ] All unit tests pass
- [ ] Code coverage > 80%
- [ ] No test failures
- [ ] Integration tests pass (if applicable)

**Best Practices:**
- [ ] No overlayering detected
- [ ] CoC patterns verified
- [ ] Naming conventions enforced
- [ ] Documentation requirements met

---

## Testing Strategy

### Unit Test Template

```
public class ExpenseReportApprovalTest
{
    // Arrange: Set up test data
    // Act: Execute the code being tested
    // Assert: Verify results

    [TestMethod]
    public void testApprovalStatusUpdate_ManagerApproves()
    {
        // Arrange
        ExpenseReport expenseReport = new ExpenseReport();
        expenseReport.Amount = 6000;
        expenseReport.SubmitterUserId = "USER1";
        expenseReport.ManagerUserId = "MANAGER1";
        
        // Act
        expenseReport.ApproveExpense("MANAGER1", "Approved");
        
        // Assert
        Assert.AreEqual(ExpenseReportStatus::Approved, expenseReport.Status);
        Assert.AreEqual("MANAGER1", expenseReport.ApproverUserId);
    }

    [TestMethod]
    public void testApprovalNotification_SentToSubmitter()
    {
        // Arrange
        ExpenseReport expenseReport = CreateTestExpenseReport();
        
        // Act
        expenseReport.ApproveExpense("MANAGER1", "Approved");
        
        // Assert
        // Verify notification was sent to submitter
        Assert.IsTrue(NotificationWasSent("USER1", NotificationType::ApprovalNotification));
    }

    [TestMethod]
    [ExpectedException(typeof(DuplicateKeyException))]
    public void testDuplicateApproval_ThrowsException()
    {
        // Arrange
        ExpenseReport expenseReport = CreateTestExpenseReport();
        expenseReport.ApproveExpense("MANAGER1", "Approved");
        
        // Act (should throw)
        expenseReport.ApproveExpense("MANAGER1", "Approved");
    }

    [TestMethod]
    public void testEdgeCase_ManagerIsSubmitter()
    {
        // Arrange
        ExpenseReport expenseReport = new ExpenseReport();
        expenseReport.Amount = 6000;
        expenseReport.SubmitterUserId = "USER1";
        expenseReport.ManagerUserId = "USER1"; // Same person
        
        // Act / Assert
        Assert.IsTrue(expenseReport.RequiresSecondApprover());
    }
}
```

### Test Scenario Definition

For each feature, define:

```
FEATURE: Expense Report Approval

TEST SCENARIOS:

Scenario 1: Normal Approval
  Given: Expense report > $5,000, submitted by USER1
  When: Manager approves
  Then: Status = Approved, notification sent to USER1

Scenario 2: Normal Rejection
  Given: Expense report > $5,000, submitted by USER1
  When: Manager rejects with comment
  Then: Status = Rejected, comment stored, notification sent

Scenario 3: Conflict of Interest (Manager = Submitter)
  Given: Expense report $5,001, submitted by MANAGER1
  When: System processes
  Then: Second approval required from manager's manager

Scenario 4: Concurrent Approvals
  Given: Expense report waiting approval
  When: Two managers approve simultaneously
  Then: First approval wins, second receives "already approved" message

Scenario 5: Post-Approval Modification
  Given: Expense report approved
  When: Submitter modifies amount
  Then: Approval status reset, requires re-approval

Scenario 6: Manager Deleted
  Given: Expense report approved by MANAGER1
  When: MANAGER1 user is deleted
  Then: Approval remains valid (historical record)

Edge Cases:
- What if expense amount is exactly $5,000? ($5,001 approval required? Or not?)
- What if manager is on vacation? (Delegate approval?)
- What if multiple currencies? (Convert for comparison?)
- What if fiscal period closed? (Block or allow?)
```

---

## Common Patterns

### Pattern 1: Form Extension with Business Logic

**Use case:** Extend existing form with new approval workflow

```x++
// EXTENSION OF ExpenseReportForm
[ExtensionOf(formStr(ExpenseReport))]
final class ExpenseReportForm_Approval_Extension
{
    // Override design method to add new control
    public void design()
    {
        // Call base design
        next design();
        
        // Add new approval status group
        FormGroupControl approvalGroup = this.AddGroup("ApprovalGroup", "Approval");
        approvalGroup.AddStringControl(ApprovalStatus, "Status");
        approvalGroup.AddStringControl(ApproverUserId, "Approved By");
    }

    // Override init to populate approval data
    public void init()
    {
        next init();
        
        this.PopulateApprovalData();
    }

    // Business logic
    private void PopulateApprovalData()
    {
        ExpenseReport expenseReport = this.GetExpenseReport();
        
        if (expenseReport.Amount > 5000)
        {
            this.ShowApprovalSection();
        }
    }
}
```

### Pattern 2: Class Extension with New Method

**Use case:** Add new approval logic to existing ExpenseReport entity

```x++
[ExtensionOf(tableStr(ExpenseReport))]
final class ExpenseReport_Approval_Extension
{
    // New method to handle approval
    public void ApproveExpense(UserId approver, str comment)
    {
        this.validateApproval(approver);
        
        ttsBegin;
        try
        {
            this.ApprovalStatus = ExpenseReportStatus::Approved;
            this.ApproverUserId = approver;
            this.ApprovalDate = today();
            this.ApprovalComment = comment;
            this.update();
            
            // Send notification
            this.SendApprovalNotification(approver);
            
            ttsCommit;
        }
        catch (Exception ex)
        {
            ttsAbort;
            error(strFmt("Approval failed: %1", ex.Message));
        }
    }

    // Validation
    private void validateApproval(UserId approver)
    {
        // Check if already approved
        if (this.ApprovalStatus == ExpenseReportStatus::Approved)
        {
            throw new DuplicateKeyException("Already approved");
        }

        // Check authority
        if (!this.CanApprove(approver))
        {
            throw new AccessViolationException("Not authorized to approve");
        }
    }

    // Send notification
    private void SendApprovalNotification(UserId approver)
    {
        SysEmailTable emailTable = SysEmailTable::find(SysEmailId::ApprovalNotification);
        
        // Compose email
        String body = strFmt("Expense report %1 has been approved", this.ExpenseReportId);
        
        // Send to submitter
        SysEmailSender::SendEmail(this.SubmitterUserId, body, emailTable);
    }
}
```

### Pattern 3: OData Integration for External Approval

**Use case:** Integrate with external system for approval workflow

```x++
public class ExpenseReportApprovalService
{
    private str externalApiUrl = "https://approval.example.com/api";

    public void RequestExternalApproval(ExpenseReportId reportId)
    {
        ExpenseReport expenseReport = ExpenseReport::find(reportId);
        
        if (expenseReport.Amount < 10000)
        {
            return; // Only for high-value expenses
        }

        try
        {
            // Call external approval service
            HttpRequest request = new HttpRequest();
            request.url(strFmt("%1/request-approval", this.externalApiUrl));
            request.setHeader("Content-Type", "application/json");
            
            // Build request JSON
            str jsonBody = this.BuildApprovalRequest(expenseReport);
            request.body(jsonBody);
            
            // Send request
            HttpResponse response = request.post();
            
            if (response.statusCode() == 200)
            {
                // Update local status
                expenseReport.ExternalApprovalId = response.contentAsJson().get("approvalId");
                expenseReport.update();
            }
            else
            {
                throw new Exception("External approval service returned error");
            }
        }
        catch (Exception ex)
        {
            // Log error and notify
            SysOperationLogEntry::CreateError(ex);
            throw;
        }
    }

    private str BuildApprovalRequest(ExpenseReport expenseReport)
    {
        // Build JSON for external API
        Map jsonData = new Map(Types::String, Types::AnyType);
        jsonData.insert("expenseId", expenseReport.ExpenseReportId);
        jsonData.insert("amount", expenseReport.Amount);
        jsonData.insert("submitter", expenseReport.SubmitterUserId);
        jsonData.insert("description", expenseReport.Description);
        
        return mapToJson(jsonData);
    }
}
```

---

## Best Practices

### 1. Standardize Everything

**What to standardize:**
- Prompt templates (copy, don't create from scratch)
- Code structure (naming, organization, comments)
- PR templates (same format every time)
- Test cases (same structure)
- Definition of Done checklist

**Why:** Consistency reduces variation, catches errors earlier, trains AI to generate better code

### 2. Use Claude as Reviewer First, Generator Second

**Best practice:**
1. Use Claude to generate code skeleton
2. Developer implements business logic
3. **Use Claude to review** before submitting PR
4. Only then do peer review

**Why:** Catches 70% of common issues before human review, saves time, improves code quality

### 3. Enforce Extension-Only Development

**Rule:** No overlayering. Use Chain of Customization (CoC) patterns only.

**Why:**
- Easier to update base code
- Cleaner for version upgrades
- Maintenance nightmare otherwise
- Use Claude to verify this in code review

### 4. Automated Gates Are Non-Negotiable

**Minimum gates:**
- [ ] Compilation (zero errors/warnings)
- [ ] Unit tests pass
- [ ] Code coverage > 80%
- [ ] Static analysis clean
- [ ] No overlayering detected

**Why:** Catches stupid mistakes automatically, frees humans to review logic not syntax

### 5. Test-Driven Workflow

**Order of work:**
1. Write test cases first (from requirements)
2. Generate code skeleton
3. Implement code to pass tests
4. Code review
5. Merge

**Why:** Forces clarity on requirements, ensures coverage, reduces rework

### 6. Document Edge Cases Explicitly

When generating code, **always ask Claude to identify edge cases:**
```
Edge cases identified:
- Manager = Submitter → Need second approval
- Concurrent modifications → Optimistic locking
- Fiscal period closed → Block submission
- Large volumes → Batch processing required
```

Then ensure each edge case has:
- [ ] Code that handles it
- [ ] Test case that validates it
- [ ] Documentation of behavior

---

## Integration Scenarios

Claude can assist with:

### OData Integrations
- Generate OData query code
- Review API authentication
- Validate request/response handling

### Dual-Write Integrations (D365 ↔ D365 CE)
- Generate dual-write sync code
- Review conflict resolution
- Test data consistency

### Power Platform Integrations
- Generate Power Automate flow code
- Review D365 FO plugin logic
- Test cloud connector setup

### Azure Integrations
- Generate code for Service Bus, Storage, Functions
- Review security (managed identity, secrets)
- Validate error handling and retries

---

## Workflow Automation (CI/CD)

### Recommended Gates

```
PR Submitted
  ↓
[LINT CHECK] Code style, naming conventions
  ↓
[COMPILE CHECK] Zero errors, zero warnings
  ↓
[UNIT TESTS] >80% coverage, all pass
  ↓
[STATIC ANALYSIS] Security, performance rules
  ↓
[AI REVIEW] Claude review gates (can be automated)
  ↓
[PEER REVIEW] Human review required
  ↓
[APPROVAL] Tech lead sign-off
  ↓
[MERGE] Automatic when all gates pass
  ↓
[DEPLOY] To test environment
  ↓
[SMOKE TESTS] Automated sanity checks
```

### AI-Assisted Gates

These can be automated (CI pipeline calls Claude API):

1. **Code Quality Gate**
   - Input: New code
   - Claude: Reviews against best practices
   - Output: Pass/Fail

2. **Security Gate**
   - Input: Code + list of security rules
   - Claude: Checks for vulnerabilities
   - Output: Issues found or Pass

3. **Test Coverage Gate**
   - Input: Code + unit tests
   - Claude: Verifies edge cases covered
   - Output: Coverage assessment

---

## Getting Help

When using Claude for D365 FO development:

**For code generation:**
- Provide clear requirements
- List constraints and edge cases
- Specify integration type
- Ask for test scenarios

**For code review:**
- Paste complete method/class
- Describe context
- List specific concerns
- Ask for security/performance validation

**For troubleshooting:**
- Provide full exception + stack trace
- Share relevant code
- Describe how to reproduce
- List recent changes

