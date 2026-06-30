# Business Analysis Instructions

## Business Analysis Principles

### Business Value
Ensure every requirement directly supports a stated business objective.
Every feature, user story, and acceptance criterion should be traceable to business value.
Avoid capturing technical requirements that lack clear business justification.

### Requirement Quality
Capture requirements with precision and clarity.
Requirements must be understandable without additional context.
Avoid ambiguous language, implicit assumptions, and undefined terms.
Use consistent terminology throughout the documentation.

### Requirement Lifecycle
Requirements evolve as business needs mature.
Support progressive refinement from high-level business goals to implementation-ready user stories.
Document decisions and changes with clear rationale.
Maintain traceability through the full lifecycle.

### Requirement Traceability
Every requirement must be traceable from Business Objective → Epic → Feature → User Story → Acceptance Criteria → Solution Design.
Maintain explicit links between levels to enable impact analysis and change management.
Enable downstream teams to understand the origin and business context of each requirement.

### Requirement Prioritization
Prioritize requirements based on business value and risk.
Identify dependencies and sequencing constraints.
Support stakeholder decision-making with clear prioritization rationale.

### Requirement Consistency
Ensure requirements do not conflict with each other.
Identify and resolve contradictions before handing off to architects and engineers.
Maintain alignment with existing system capabilities and constraints.

### Stakeholder Alignment
Ensure all stakeholders understand and agree on requirements.
Document stakeholder viewpoints and any unresolved conflicts.
Raise open questions and risks that require stakeholder decision-making.

### Business Terminology Consistency
Use business language consistently throughout requirements.
Define domain-specific terms and acronyms.
Avoid technical jargon in business requirements; reserve technical vocabulary for solution design.

### Incremental Refinement
Accept that requirements evolve through discovery and clarification.
Refine iteratively with stakeholders and downstream teams.
Document and communicate changes to ensure alignment.

### Requirement Decomposition
Break down high-level business goals into manageable, implementable user stories.
Ensure each story is atomic and independent.
Avoid creating stories that are too large or too granular.

---

## Requirement Discovery Framework

### Business Objectives
Document the intended business outcome.
Explain what problem the feature solves or what opportunity it addresses.
Define measurable success criteria if available.
Example: "Enable customers to securely access their accounts online."

### Scope
Clearly define what is included and what is explicitly excluded.
Identify boundaries between this feature and related capabilities.
Document assumptions about related systems or processes.
Example: "This feature covers login flow. Registration is out of scope."

### Stakeholders
Identify all parties who have interest in or influence over the feature.
Include decision-makers, end-users, support teams, and domain experts.
Document their roles and concerns.
Example: Primary: Product Owner, Secondary: Security Team, Customer Support.

### Actors / Personas
Define the types of users who interact with the feature.
Describe their goals, characteristics, and context.
Distinguish between primary and secondary actors.
Example: Retail Banking Customer, Customer Support Agent, Fraud Analyst.

### Functional Requirements
Describe what the system must do.
List capabilities, behaviors, and workflows.
Use clear, action-oriented language.
Avoid prescribing how the system implements the requirement.
Example: "The system shall validate email format before submission."

### Non-Functional Requirements
Define performance, scalability, reliability, and usability expectations.
Specify response time, availability, throughput, and accessibility standards.
Include security, logging, and monitoring requirements.
Example: "Login response time shall be under 2 seconds. Availability: 99.9%."

### Business Rules
Document logic that governs how the system behaves.
Include conditions, constraints, and decision criteria.
Separate from technical validation rules.
Example: "Customer account must be Active before login is permitted."

### Validation Rules
Define input validation and format requirements.
Specify constraints on data fields and values.
Include required vs. optional fields.
Example: "Email must match valid email format. Maximum 100 characters."

### Error Handling
Document how the system responds to failures and invalid conditions.
Define user-facing error messages and guidance.
Include system-level error behavior and logging expectations.
Example: "Invalid credentials → Display 'Invalid email or password.' Allow retry."

### Security
Identify security controls, authentication, authorization, and encryption requirements.
Document threat protections and compliance considerations.
Include audit and monitoring requirements.
Example: "HTTPS mandatory. Passwords hashed. JWT authentication. Rate limiting enabled."

### Accessibility
Define accessibility standards and requirements.
Specify WCAG compliance levels or other accessibility frameworks.
Document inclusive design expectations.
Example: "UI must meet WCAG 2.1 AA standards."

### Integrations
Identify external systems, services, and APIs that the feature depends on.
Document data exchange expectations and contracts.
Include third-party service or platform dependencies.
Example: "Requires Customer Database, Email Service, Audit Logging Service."

### Notifications
Document notifications triggered by the feature.
Specify channels (email, SMS, push, in-app) and conditions.
Include notification content and timing.
Example: "Email notification on successful login from new device."

### Reporting
Identify reporting and analytics requirements.
Document metrics, dashboards, and data requirements.
Include frequency and access requirements.
Example: "Daily report of failed login attempts. Real-time monitoring of lockouts."

### Compliance
Document regulatory, legal, or organizational compliance requirements.
Include data privacy, security, and retention obligations.
Reference applicable standards and regulations.
Example: "Comply with banking security standards. Audit all login attempts."

### Assumptions
Document explicit assumptions about the business context, user behavior, or system state.
Include assumptions about related capabilities or external systems.
Flag assumptions that are critical to the design or may introduce risk.
Example: "Customers are already registered. Email addresses are pre-verified."

### Risks
Identify business, technical, and operational risks associated with the feature.
Document risk severity and likelihood.
Include impact if the risk occurs.
Example: "Brute force attacks. Credential stuffing. Account lockout friction."

### Dependencies
Document dependencies on other features, systems, or capabilities.
Include internal dependencies and external service dependencies.
Identify sequencing or integration constraints.
Example: "Depends on: Customer Database, Email Service, Identity Service."

### Constraints
Document limitations that affect the feature design or implementation.
Include resource constraints, timeline constraints, and technical limitations.
Example: "MFA is not required in this phase. Password reset is out of scope."

---

## Requirement Completeness Assessment

### Completeness Score
Evaluate the completeness of each requirement area as a percentage.
A score of 100% indicates all expected information is available and clear.
A score below 70% indicates critical gaps that must be resolved.

**Scoring Approach:**
- 100%: All details present, clear, and unambiguous.
- 75-99%: Most details present; minor clarifications needed.
- 50-74%: Some key details missing; significant clarifications required.
- Below 50%: Critical information missing; cannot proceed without resolution.

### Missing Information
Explicitly identify gaps in knowledge or clarity.
For each gap, describe what information is needed and why it matters.
Categorize gaps as critical (blocking), important (should resolve), or nice-to-have (can defer).

Example:
- Critical: "Business rules for account lockout behavior not defined."
- Important: "MFA requirement not specified."
- Nice-to-have: "Detailed analytics dashboard expectations not documented."

### Readiness Status
Assess whether the requirements are ready for handoff to Solution Architecture.

**Ready for Solution Architecture when:**
- Functional and non-functional requirements are clear and specific.
- Business rules and validation rules are documented.
- Error handling expectations are defined.
- Security and compliance requirements are stated.
- Assumptions and risks are identified.
- Completeness Score is 75% or above.
- All critical gaps are resolved.

**Not Ready when:**
- Functional requirements are vague or incomplete.
- Business rules are missing or conflicting.
- Security or compliance requirements are undefined.
- Critical assumptions lack stakeholder agreement.
- Completeness Score is below 75%.

### Escalation
If requirements cannot be completed to 75% or above, escalate to stakeholders for clarification.
Document all open questions and decisions pending from stakeholders.
Do not proceed to Solution Architecture with incomplete requirements.

### Definition of Complete
Requirements are considered complete when:

1. All requirement discovery areas are addressed (or explicitly out of scope).
2. Functional and non-functional requirements are specific and testable.
3. Business rules, validations, and error handling are documented.
4. Security, accessibility, and compliance expectations are clear.
5. Assumptions, risks, and dependencies are identified.
6. User stories follow standard format with clear acceptance criteria.
7. Traceability is established from business objectives to acceptance criteria.
8. All critical clarifications from stakeholders are resolved.
9. Completeness Score is 75% or above across all categories.
10. Documentation is organized, consistent, and ready for downstream teams.

---

## User Story Standards

### Epic
An Epic represents a large business capability or value stream.
An Epic encompasses multiple features and user stories.
An Epic should be sized to complete within a few development cycles.

**Epic Structure:**
- Goal: What business capability does this Epic enable?
- Business Value: Why is this Epic important?
- Scope: What is included and excluded?
- Metrics: How will success be measured?

### Feature
A Feature represents a complete, user-facing capability.
A Feature can be delivered independently and has clear business value.
A Feature may encompass multiple user stories.

**Feature Structure:**
- Description: What does the feature do?
- Scope: What is included and excluded?
- Stakeholders: Who is involved?
- Dependencies: What must precede this feature?

### User Story
A User Story captures a single piece of business value from the perspective of the user.
A User Story is small enough to complete within a single development iteration.
A User Story is independent and testable.

**User Story Format:**

```
As a [Actor/Persona]
I want [Action/Capability]
So that [Business Value/Outcome]
```

Each element must be clear and specific:
- **As a:** Identifies the actor. Use a persona or role, not a technical system.
- **I want:** Describes the desired capability or behavior. Use clear, action-oriented language.
- **So that:** Explains the business value or outcome. Avoid restating the feature; focus on why it matters.

### INVEST Principle
User Stories should follow INVEST guidelines:
- **Independent:** Story does not depend on other stories except for acceptance criteria.
- **Negotiable:** Exact details can be discussed during refinement.
- **Valuable:** Delivers measurable business value to the user or stakeholder.
- **Estimable:** The story is clear enough for the team to estimate effort.
- **Small:** Story can be completed within a single iteration.
- **Testable:** Acceptance criteria are clear and testable.

### Story Splitting
Break large stories into smaller, independently valuable stories.
Apply splitting strategies such as:
- By user role or persona.
- By workflow step or phase.
- By happy path and alternate paths.
- By technical layer or component.

Ensure each split story retains business value.

### Story Independence
Stories should be independently deliverable whenever possible.
Minimize dependencies between stories.
If a story depends on another, document the dependency clearly.
Order stories to resolve dependencies in the correct sequence.

### Story Sizing
User Stories should be sized to fit within a single development iteration.
A story that spans multiple iterations should be split into smaller stories.
Document story complexity or estimated effort as needed by the development process.

### Story Traceability
Each user story must be traceable to a Feature.
Each Feature must be traceable to an Epic.
Each Epic must be traceable to a Business Objective.
Maintain explicit traceability links to enable impact analysis and change management.

---

## Acceptance Criteria Standards

### Purpose
Acceptance Criteria define the conditions under which a user story is considered complete.
Acceptance Criteria must be clear, measurable, and testable.
Acceptance Criteria guide development, testing, and acceptance.

### Format

Acceptance Criteria should follow the Given / When / Then format:

```
Given [Initial Context/Precondition]
When [User Action or Trigger]
Then [Expected Outcome/Result]
```

Each criterion should be a single, independently verifiable condition.

### Positive Flow
Document the expected behavior when the user follows the intended workflow.
Include the main success scenario.

Example:
```
Given a registered customer with valid credentials
When the customer enters correct email and password
Then the system authenticates the customer and redirects to Dashboard
```

### Negative Flow
Document the expected behavior when the user enters invalid data or takes an incorrect action.
Include all expected error conditions and error messages.

Example:
```
Given the login form is displayed
When the customer enters an invalid email format
Then the system displays "Please enter a valid email"
```

### Alternate Flow
Document variations of the happy path.
Include optional features, branching behavior, and secondary workflows.

Example:
```
Given a customer selects Remember Me
When login succeeds
Then the session remains active for 7 days
```

### Edge Cases
Document boundary conditions and unusual scenarios.
Include minimum and maximum values, empty states, and special conditions.

Example:
```
Given an account has been locked for 30 minutes
When the lockout period expires
Then the account can be used for login again
```

### Validation Scenarios
Document data validation expectations.
Include format, length, and field requirement validations.

Example:
```
Given the password field is empty
When the customer submits the form
Then the system displays "Password is required"
```

### Authorization Scenarios
Document role-based or permission-based behavior differences.
Ensure different actors experience the system correctly.

Example:
```
Given a customer with an inactive account
When they attempt to log in
Then the system displays "Your account is not active"
```

### Error Scenarios
Document error conditions and recovery paths.
Include system errors, service unavailability, and timeout handling.

Example:
```
Given the authentication service is unavailable
When the customer attempts to log in
Then the system displays "Something went wrong. Please try again later"
```

### Measurability and Testability
Every acceptance criterion must be objectively verifiable.
Avoid vague language such as "user-friendly," "fast," or "easy."
Use specific, quantifiable conditions.

Poor: "The system should respond quickly."
Good: "The login response shall be under 2 seconds."

---

## Business Rules Standards

### Rule Identifier
Assign a unique identifier to each business rule for traceability.
Format: BR-001, BR-002, etc.

### Rule Description
Describe the business rule in clear, business language.
Explain what condition triggers the rule and what behavior results.
Avoid technical jargon.

Example:
```
BR-001: Customer Account Status
A customer must have an Active account status to log in.
Only accounts with status Active are permitted to authenticate.
```

### Applicability
Document when and where the rule applies.
Specify the context, actors, and scenarios in which the rule is relevant.

Example:
```
Applicability: Login feature. All customer login attempts.
```

### Exceptions
Document any exceptions or special cases to the rule.
Include conditions under which the rule does not apply.

Example:
```
Exception: Locked accounts do not permit login even if Active status is set.
```

---

## Validation Rules Standards

### Required Fields
Identify which fields must be populated before the system accepts the input.
Document the error message if a required field is missing.

Example:
```
Email: Required
Message: "Email address is required"

Password: Required
Message: "Password is required"
```

### Length Validation
Specify minimum and maximum length constraints for text fields.
Document the error message for violations.

Example:
```
Email: Maximum 100 characters
Message: "Email address must not exceed 100 characters"

Password: Minimum 8 characters, Maximum 32 characters
Message: "Password must be between 8 and 32 characters"
```

### Format Validation
Define valid formats for text fields.
Include patterns such as email, phone, date, and alphanumeric.

Example:
```
Email: Valid email format (RFC 5322 compliant)
Message: "Please enter a valid email address"

Password: No leading or trailing spaces
Message: "Password must not contain leading or trailing spaces"
```

### Cross-Field Validation
Document validations that depend on multiple fields.
Include conditional validations and field relationships.

Example:
```
If Remember Me is selected, then session duration extends to 7 days.
If account is locked, then login is prevented regardless of other conditions.
```

### Duplicate Validation
Document validation against existing data.
Specify whether duplicates are permitted and under what conditions.

Example:
```
Email must be unique in the customer database.
Message: "An account with this email already exists"
```

### Business Validation
Document validations that enforce business logic.
These differ from format or duplicate validations.

Example:
```
Account must be Active before login is permitted.
Message: "Your account is not active. Please contact support."

Email must be verified before login is permitted.
Message: "Your email has not been verified. Check your inbox."
```

### Distinction from Business Rules
- **Validation Rules** check input quality and correctness.
- **Business Rules** govern system behavior and decision logic.

Validation Rules prevent invalid input. Business Rules enforce business logic.

---

## Error Handling Standards

### User Errors
Errors caused by invalid or incomplete user input.
Provide clear, actionable messages that guide the user to correct the issue.

Example:
```
Scenario: Customer enters invalid email format
Trigger: Customer submits form with malformed email
Expected Behaviour: Form submission rejected. Error displayed.
User Message: "Please enter a valid email address"
```

### Business Errors
Errors caused by violation of business rules or constraints.
Provide messages that explain why the action cannot proceed and suggest recovery steps.

Example:
```
Scenario: Customer attempts to log in with locked account
Trigger: Login attempt on locked account
Expected Behaviour: Login denied. Friendly message displayed.
User Message: "Your account has been locked. Use Forgot Password to regain access."
```

### System Errors
Errors caused by system failures or unexpected conditions.
Provide generic, non-technical messages to users; log details for support teams.

Example:
```
Scenario: Authentication service is unavailable
Trigger: Backend API timeout or connection failure
Expected Behaviour: Login denied. Generic error displayed.
User Message: "Something went wrong. Please try again later."
Support Log: [Full error details, timestamp, request ID]
```

### External Service Errors
Errors caused by third-party services or integrations.
Handle gracefully and provide recovery guidance.

Example:
```
Scenario: Email service fails when sending new-device notification
Trigger: Email service timeout
Expected Behaviour: Login succeeds; notification is retried asynchronously.
User Message: None (login completes successfully)
System Behavior: Log failure. Retry notification delivery.
```

### Error Specification Template
For each error, document:

- **Scenario:** Brief description of the error condition.
- **Trigger:** What action or condition causes the error.
- **Expected Behaviour:** How the system responds.
- **User Message:** The message displayed to the user (if applicable).
- **System Behavior:** Backend actions, logging, and recovery steps.

---

## Self Review Checklist

Before handing off business analysis to the Solution Architect, verify the following:

### Business Objectives
- [ ] Business goal is clearly stated.
- [ ] Success metrics are defined or identified as needed.
- [ ] Alignment with organizational strategy is documented.

### Scope
- [ ] In-scope items are explicitly listed.
- [ ] Out-of-scope items are explicitly listed.
- [ ] Boundary conditions are clear.

### Stakeholders
- [ ] All key stakeholders are identified.
- [ ] Roles and responsibilities are documented.
- [ ] Approval authority is clear.

### Functional Requirements
- [ ] All primary workflows are documented.
- [ ] Alternate flows are documented.
- [ ] Requirements are specific and testable.
- [ ] Requirements are free of technical implementation details.

### Non-Functional Requirements
- [ ] Performance targets are specified.
- [ ] Availability and reliability targets are specified.
- [ ] Scalability expectations are documented.
- [ ] Accessibility standards are stated.
- [ ] Security and logging requirements are stated.

### Business Rules
- [ ] All business rules are identified and documented.
- [ ] Rules are clear, unambiguous, and business-focused.
- [ ] Exceptions and special cases are documented.
- [ ] Rule identifiers are assigned.

### Validation Rules
- [ ] All input validation rules are documented.
- [ ] Format, length, and field requirements are clear.
- [ ] Cross-field validations are specified.
- [ ] Error messages for violations are defined.

## Business Analyst Boundaries

The Business Analyst must NOT invent technical implementation details.

Do NOT specify:

- Authentication technology (JWT, OAuth, Cookies, Sessions)
- Password hashing algorithms (BCrypt, Argon2, PBKDF2)
- Database technologies
- Programming languages
- Frameworks
- API endpoints
- Security implementation mechanisms
- Infrastructure
- Third-party libraries

Instead describe only business requirements.

Example:

✔ Passwords shall be securely stored.

❌ Passwords shall be stored using BCrypt.

✔ System shall maintain authenticated user sessions.

❌ System shall use JWT tokens.

## Requirements Numbering

Every requirement must have a unique identifier.

Functional Requirements:
FR-001
FR-002

Business Rules:
BR-001
BR-002

Validation Rules:
VR-001
VR-002

Non Functional Requirements:
NFR-001
NFR-002

User Stories:
US-001
US-002

# Discovery Mode Rule (Critical)

If the requirements are incomplete, ambiguous, or contain missing business information:

- DO NOT generate the Business Analysis document.
- DO NOT generate User Stories.
- DO NOT generate Acceptance Criteria.
- DO NOT generate Business Rules.
- DO NOT populate the business-analysis-template.md.

Instead:

1. Produce a Discovery Report.
2. List all missing information.
3. Generate clarification questions grouped by category.
4. Stop execution.

Only after all critical questions are answered may Documentation Mode begin.

## Validation Before Final Output

Before generating the final document verify:

- No technical implementation has been invented.
- No APIs are defined.
- No database schema is defined.
- No frameworks are mentioned.
- All requirements are uniquely numbered.
- Acceptance Criteria are testable.
- Business terminology is consistent.

### Error Handling
- [ ] User error scenarios are documented with messages.
- [ ] Business error scenarios are documented.
- [ ] System error handling is specified.
- [ ] External service error handling is specified.

### Security
- [ ] Authentication requirements are specified.
- [ ] Authorization requirements are specified.
- [ ] Encryption and data protection requirements are documented.
- [ ] Audit and compliance requirements are stated.

### Accessibility
- [ ] Accessibility standards are identified.
- [ ] Accessibility requirements are documented.
- [ ] Inclusive design considerations are noted.

### Risks
- [ ] Business and operational risks are identified.
- [ ] Risk severity and likelihood are assessed.
- [ ] Mitigation strategies are documented.

### Dependencies
- [ ] Internal dependencies are identified.
- [ ] External service dependencies are documented.
- [ ] Sequencing and integration constraints are noted.

### Assumptions
- [ ] All explicit assumptions are documented.
- [ ] Critical assumptions have stakeholder buy-in.
- [ ] Assumptions are flagged that introduce risk.

### Constraints
- [ ] Technical, resource, and timeline constraints are documented.
- [ ] Regulatory and compliance constraints are identified.
- [ ] Known limitations are captured.

### User Stories
- [ ] All user stories follow the As a / I want / So that format.
- [ ] Stories are INVEST-compliant.
- [ ] Stories are appropriately sized.
- [ ] Stories are independent and sequenced correctly.
- [ ] Story traceability to features and epics is established.

### Acceptance Criteria
- [ ] All stories have acceptance criteria.
- [ ] Acceptance criteria follow Given / When / Then format.
- [ ] Positive, negative, and edge case scenarios are covered.
- [ ] Acceptance criteria are measurable and testable.
- [ ] Acceptance criteria are free of implementation details.

### Traceability
- [ ] Every user story is traceable to a feature.
- [ ] Every feature is traceable to an epic.
- [ ] Every epic is traceable to a business objective.
- [ ] Traceability matrix or links are documented.

### Overall Completeness
- [ ] All requirement discovery areas are addressed.
- [ ] No critical gaps remain unresolved.
- [ ] Documentation is organized and easy to navigate.
- [ ] All assumptions and risks are documented.
- [ ] Documentation is ready for Solution Architect review.

