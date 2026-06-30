# Feature Information

## Feature Name

Customer Login

## Module

Authentication

## Priority

High

## Business Goal

Allow registered retail banking customers to securely access the online banking application using their registered email address and password.

## Business Value

- Protect customer accounts from unauthorized access.
- Provide a secure and seamless authentication experience.
- Reduce fraud through secure authentication mechanisms.
- Improve customer satisfaction by providing a fast and reliable login experience.

## Background

The banking application currently does not provide an authentication mechanism for customers. Customers must be able to securely log in before accessing account information, transactions, statements, and other banking services.

---

# Scope

## In Scope

- Login using registered email address and password.
- Email format validation.
- Password validation.
- Remember Me functionality.
- Show/Hide Password option.
- Forgot Password navigation.
- Session management.
- Account lock after multiple failed login attempts.
- Login audit logging.
- Email notification for login from a new device.

## Out of Scope

- Customer Registration.
- Reset Password implementation.
- Multi-Factor Authentication (future enhancement).
- Biometric Login.
- Social Login.

---

# Stakeholders

## Primary Stakeholder

Retail Banking Customers

## Business Owner

Digital Banking Department

## End Users

Registered Retail Banking Customers

---

# Actors / Personas

## Retail Banking Customer

A registered customer who wants to securely access their banking dashboard to perform banking operations.

## Customer Support Executive

Supports customers who experience login-related issues such as locked accounts or password recovery.

---

# Functional Requirements

- Customer shall log in using registered email address and password.
- System shall validate email format before authentication.
- Password shall be validated before authentication.
- Successful login shall redirect customer to Dashboard.
- Failed login attempts shall be recorded.
- Remember Me checkbox shall extend session duration.
- Forgot Password link shall redirect to password recovery.
- Password field shall support Show/Hide Password.
- Account shall be locked after five consecutive failed login attempts.
- Customer shall receive an email notification after login from a new device.

---

# Non Functional Requirements

## Performance

- Login response time shall be less than 2 seconds.

## Availability

- Authentication service availability shall be 99.9%.

## Scalability

- Authentication service shall support at least 10,000 concurrent users.

## Accessibility

- UI shall comply with WCAG 2.1 AA.

## Security

- HTTPS shall be mandatory.
- Passwords shall never be stored in plain text.
- JWT authentication shall be used.

---

# Business Rules

- Customer account must be Active.
- Customer email must be verified.
- Maximum five failed login attempts are allowed.
- Locked accounts remain locked for 30 minutes.
- Remember Me extends session validity to seven days.

---

# Validation Rules

## Email

- Required.
- Valid email format.
- Maximum length: 100 characters.

## Password

- Required.
- Minimum length: 8 characters.
- Maximum length: 32 characters.
- Must not contain spaces.

---

# Error Handling

- Invalid email format → "Please enter a valid email address."
- Empty password → "Password is required."
- Invalid credentials → "Invalid email or password."
- Locked account → "Your account has been locked for 30 minutes."
- Server unavailable → "Something went wrong. Please try again later."

---

# Security Requirements

- JWT authentication.
- HTTPS only.
- Secure password hashing using BCrypt.
- Rate limiting for login requests.
- CAPTCHA after five failed attempts.
- Audit every login attempt.
- Session timeout after 15 minutes of inactivity.
- CSRF protection where applicable.

---

# Accessibility Requirements

- WCAG 2.1 AA compliance.
- Keyboard accessible.
- Screen reader compatible.
- Proper labels for all form controls.
- Sufficient color contrast.
- Focus indicators for interactive controls.

---

# Integrations

- Identity Service.
- Customer Database.
- Audit Logging Service.
- Email Notification Service.

---

# Notifications

- Email notification for successful login from a new device.
- Email notification after account lock.
- Security alert for suspicious login attempts.

---

# Reporting

- Daily login activity report.
- Failed login attempts report.
- Locked account report.
- Security audit report.

---

# UI Behaviour

- Email field.
- Password field.
- Show/Hide Password toggle.
- Remember Me checkbox.
- Login button.
- Forgot Password link.
- Inline validation messages.
- Loading indicator while authenticating.
- Disable Login button during request processing.

---

# Wireframes / Mockups

## Figma Link

To be provided.

## Images

None.

## Screenshots

None.

---

# Success Criteria

- Registered customers can log in successfully.
- Login response time remains under 2 seconds.
- Failed login attempts are correctly tracked.
- Accounts lock after five consecutive failures.
- Login audit records are generated.
- New device login notifications are sent successfully.

---

# Assumptions

- Customer registration already exists.
- Password reset feature exists separately.
- Email verification is completed during registration.
- Identity service is available.

---

# Risks

- Brute force attacks.
- Credential stuffing.
- Phishing attacks.
- Authentication service downtime.
- Customer frustration due to account lock.

---

# Dependencies

- Identity Service.
- Customer Database.
- Email Service.
- Audit Logging Service.
- Notification Service.

---

# Constraints

- Banking security policies must be followed.
- GDPR and banking compliance regulations apply.
- JWT authentication is mandatory.
- HTTPS is mandatory.

---

# Open Questions

- Should Multi-Factor Authentication be mandatory?
- Should biometric authentication be added later?
- Should corporate customers have a separate login flow?
- Should account unlock require customer support after multiple lock cycles?

---

# Additional Notes

This feature represents the initial authentication capability for the Online Banking Application and serves as the entry point for all customer-facing banking services.