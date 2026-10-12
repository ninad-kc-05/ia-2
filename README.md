# Software Engineering — Exam Preparation
## Modules 4, 5 and 6

This README contains priority-wise questions, detailed answers, examples, testing techniques, formulas, and revision notes for Software Engineering exam preparation.

### Priority Guide

- **Priority 1:** Prepare first.
- **Priority 2:** Prepare next.
- **Priority 3:** Additional revision.

> **Note:** The priorities are study recommendations based on the uploaded question banks, not predictions of the examination paper. Verify the final module scope against the official SEE syllabus.

---

# CONTENTS

1. [Priority-Wise Question List](#1-priority-wise-question-list)
2. [Module 4 - Software Design](#2-module-4---software-design)
3. [Module 5 - Software Testing](#3-module-5---software-testing)
4. [Module 6 - Risk and Quality Management](#4-module-6---risk-and-quality-management)
5. [Formula Revision Sheet](#5-formula-revision-sheet)
6. [Last-Minute Revision Checklist](#6-last-minute-revision-checklist)
7. [Answer-Writing Strategy](#7-answer-writing-strategy)

---

# 1. PRIORITY-WISE QUESTION LIST

## Priority 1 - Prepare First

### Module 4 - Software Design

1. Explain cohesion and its different types.
2. Explain coupling and its different types with examples.

### Module 5 - Software Testing

3. Differentiate between Black Box Testing and White Box Testing.
4. Explain Basis Path Testing with a suitable example.
5. Calculate Cyclomatic Complexity for a given program and identify independent paths.
6. Explain Boundary Value Analysis and Equivalence Class Partitioning.
7. Explain different software testing strategies.

### Module 6 - Risk and Quality Management

8. Explain software risk and its different types. Explain the RMMM plan with an example.
9. Explain Software Quality Assurance (SQA) and its process.
10. Explain Software Configuration Management (SCM), Version Control, and Change Control.

## Priority 2 - Prepare Next

### Module 4

- Explain software design principles.
- Explain effective modular design.
- Differentiate between cohesion and coupling.
- Explain different architectural styles.
- Explain the qualities of good software design.
- What is modularity? Explain its advantages.
- Explain data-centered architecture.

### Module 5

- Differentiate between Alpha Testing and Beta Testing.
- Explain Unit Testing and Integration Testing.
- Explain the software testing process.
- Explain the principles of software testing.
- Explain different White Box Testing techniques.
- Explain different types of software testing.

### Module 6

- Explain software risk and its categories.
- Explain an RMMM plan with a suitable example.
- Explain the steps involved in SCM.
- Differentiate between FTR and Walkthrough.
- Prepare an RMMM plan for a Student Attendance System.
- Prepare an RMMM plan for Employee Turnover or Reused Software.

## Priority 3 - Additional Revision

### Module 5

- Solve the `checkDiscount(int amount)` Basis Path Testing problem.
- Solve the `swapIfGreater(int a, int b)` Cyclomatic Complexity problem.
- Apply BVA and ECP to a salary range of Rs. 10,000 to Rs. 1,00,000.

### Module 6

- Explain Software Re-engineering.
- Explain the benefits and activities of SCM.
- Explain the SQA process.

---

# 2. MODULE 4 - SOFTWARE DESIGN

## Q1. Explain Cohesion and Its Types

### Definition

Cohesion is the degree to which the elements within a software module are related to one another.

A highly cohesive module performs one specific, well-defined task.

**A good software design aims for high cohesion.**

### Types of Cohesion

The following list goes from weakest to strongest.

#### 1. Coincidental Cohesion

Unrelated tasks are grouped together without a meaningful relationship.

This is the weakest type of cohesion.

#### 2. Logical Cohesion

Tasks belonging to the same general category are grouped together. A control flag may determine which task is executed.

Example: A single module handles several types of input operations.

#### 3. Temporal Cohesion

Tasks are grouped because they occur at the same time.

Example: Initialization operations performed when a program starts.

#### 4. Procedural Cohesion

Elements are grouped because they must execute in a particular sequence, even if they do not operate on the same data.

#### 5. Communicational Cohesion

Operations are grouped because they use or modify the same data.

Example: Operations that read and update the same customer record.

#### 6. Sequential Cohesion

The output of one operation becomes the input of the next operation.

Example: Reading data, validating it, and then processing the validated data.

#### 7. Functional Cohesion

Every element contributes to one well-defined function.

This is the strongest and most desirable type of cohesion.

### Advantages of High Cohesion

- Improves readability.
- Makes testing easier.
- Simplifies maintenance.
- Improves reusability.
- Reduces the effect of changes.
- Makes module responsibilities clear.

### Disadvantages of Low Cohesion

- Makes modules difficult to understand.
- Increases maintenance effort.
- Makes testing more complicated.
- Reduces reusability.
- Makes changes more likely to affect unrelated functionality.

### Conclusion

High cohesion makes software easier to understand, test, maintain, and reuse.

---

## Q2. Explain Coupling and Its Types

### Definition

Coupling is the degree of interdependence between software modules.

A module has high coupling when it depends heavily on the internal workings or data of other modules.

**A good software design aims for low coupling.**

### Types of Coupling

#### 1. Content Coupling

One module directly accesses or modifies the internal data or logic of another module.

This is highly undesirable because it creates a strong dependency.

#### 2. Common Coupling

Multiple modules share global data.

A change to the shared data may affect several modules.

#### 3. External Coupling

Modules depend on an externally imposed format, protocol, device, or communication interface.

#### 4. Control Coupling

One module passes control information that determines the behaviour of another module.

Example: Passing a flag that tells another module which operation to execute.

#### 5. Stamp Coupling

A complete data structure is passed to a module even though the module uses only part of it.

#### 6. Data Coupling

Modules communicate by passing only the data required by the receiving module.

This is generally desirable.

#### 7. Message Coupling

Objects communicate through messages or public interfaces without depending on each other's internal implementation.

This is commonly associated with object-oriented design.

> Note: Textbooks may present a different classification or ordering. Follow the terminology used in your course notes.

### Advantages of Low Coupling

- Modules can be modified independently.
- Testing becomes easier.
- Debugging becomes simpler.
- Reusability improves.
- Changes are less likely to affect unrelated modules.
- Integration becomes easier.

### Disadvantages of High Coupling

- Changes can affect multiple modules.
- Testing becomes more difficult.
- Debugging takes more time.
- Reusability decreases.
- Integration risks increase.

### Conclusion

Low coupling reduces dependencies and makes software easier to maintain.

---

## Q3. Differentiate Between Cohesion and Coupling

### Cohesion

- Measures the relationship between elements within a module.
- Focuses on the internal structure of a module.
- High cohesion is desirable.
- Improves readability and maintainability.
- Example: A module dedicated only to calculating tax.

### Coupling

- Measures the dependencies between different modules.
- Focuses on relationships between modules.
- Low coupling is desirable.
- Reduces the impact of changes across modules.
- Example: A tax module receives required values through parameters instead of accessing another module's internal data directly.

### Important Conclusion

**High Cohesion + Low Coupling = Good Software Design.**

---

## Q4. Explain Software Design Principles

Software design principles help developers create understandable, maintainable, and reusable systems.

### 1. Abstraction

Abstraction focuses on essential characteristics while hiding unnecessary details.

Example: A user can withdraw money from an ATM without knowing the internal banking implementation.

### 2. Modularity

Modularity divides software into smaller, manageable modules.

Each module performs a specific responsibility.

### 3. Information Hiding

Information hiding keeps internal implementation details private and exposes only necessary interfaces.

This reduces dependencies between modules.

### 4. Separation of Concerns

Different responsibilities should be handled separately.

Example: User interface, business logic, and database operations should have distinct responsibilities.

### 5. Functional Independence

Modules should have high cohesion and low coupling.

This improves testing and maintenance.

### 6. Refinement

Refinement means gradually moving from a high-level design to a more detailed design.

### 7. Simplicity

A design should avoid unnecessary complexity.

Simple designs are generally easier to understand and maintain.

### 8. Reusability

Existing components should be reused when appropriate.

This can reduce development time and duplicated effort.

### 9. Consistency

Naming conventions, interfaces, and design rules should be consistent throughout the system.

### 10. Maintainability

Software should be designed so that future changes can be made with minimal effort.

---

## Q5. Explain Effective Modular Design

### Definition

Modularity means dividing a software system into smaller components with clearly defined responsibilities.

Effective modular design makes each module easier to develop, understand, test, and maintain.

### Characteristics of an Effective Module

1. Performs a specific responsibility.
2. Has high cohesion.
3. Has low coupling.
4. Hides internal implementation details.
5. Provides a clear interface.
6. Can be tested independently.
7. Minimizes unnecessary dependencies.
8. Handles errors predictably.

### Advantages

- Reduces complexity.
- Supports parallel development.
- Improves testing.
- Encourages reuse.
- Simplifies maintenance.
- Makes defects easier to isolate.
- Makes the software easier to understand.

### Example: Student Attendance System

A Student Attendance System can contain separate modules for:

- Student Management
- Attendance Recording
- Report Generation
- Authentication

Each module should communicate through well-defined interfaces instead of directly modifying another module's internal data.

---

## Q6. Explain Architectural Styles

An architectural style describes the overall organization of a software system and how its components interact.

### 1. Data-Centered Architecture

A central repository stores data accessed by different components.

Advantages:

- Centralized data management.
- Easier sharing of common information.
- Consistent access to shared data.

Disadvantages:

- The repository may become a performance bottleneck.
- A central repository can become a point of failure if redundancy is not provided.

### 2. Data-Flow Architecture

Data passes through a sequence of processing components.

Each component processes data and sends the result to the next component.

Example: A data-processing pipeline.

### 3. Call-and-Return Architecture

The system is organized into modules that call other modules.

It is commonly used in procedure-oriented systems.

### 4. Layered Architecture

The system is divided into layers, with each layer providing services to the layer above it.

Example:

- Presentation Layer
- Business Logic Layer
- Data Access Layer

Advantages:

- Clear separation of responsibilities.
- Easier maintenance.
- Improved organization.

### 5. Object-Oriented Architecture

The system is organized around objects that combine data and behaviour.

Objects interact through defined interfaces.

### 6. Client-Server Architecture

Clients request services from servers.

Example: A web browser requesting information from a web server.

---

# 3. MODULE 5 - SOFTWARE TESTING

## Q7. Differentiate Between Black Box Testing and White Box Testing

### Black Box Testing

Black Box Testing checks software behaviour without requiring knowledge of its internal implementation.

It focuses on inputs, outputs, and requirements.

Common techniques:

- Equivalence Class Partitioning
- Boundary Value Analysis
- Decision Table Testing

Advantages:

- Tests functionality from the user's perspective.
- Does not require knowledge of internal code.
- Can reveal missing or incorrect functionality.

Limitations:

- Does not show which internal paths were executed.
- Test coverage depends on the quality of specifications and test design.

### White Box Testing

White Box Testing examines the internal structure, logic, and execution paths of software.

Common techniques:

- Statement Coverage
- Branch Coverage
- Condition Coverage
- Basis Path Testing
- Loop Testing

Advantages:

- Helps identify logic errors.
- Measures code coverage.
- Can expose untested branches and paths.

Limitations:

- Usually requires knowledge of the implementation.
- Cannot independently prove that all user requirements are satisfied.

### Main Difference

Black Box Testing checks whether software behaves correctly from the outside.

White Box Testing checks whether the internal code and logic work correctly.

Both approaches are complementary.

---

## Q8. Differentiate Between Alpha Testing and Beta Testing

### Alpha Testing

- Usually performed in a controlled environment.
- Often performed by internal testers or selected internal users.
- Takes place before beta testing.
- Helps identify defects before wider distribution.
- Allows the development team to investigate failures in a controlled setting.

### Beta Testing

- Performed by selected external users.
- Takes place in real or realistic user environments.
- Usually follows alpha testing.
- Helps discover environment-specific problems.
- Provides feedback before final release.

### Conclusion

Alpha Testing identifies problems in a controlled environment, while Beta Testing evaluates the software with selected users in more realistic environments.

---

## Q9. Explain Unit Testing and Integration Testing

### Unit Testing

Unit Testing verifies an individual function, class, or module in isolation.

It aims to identify defects in small components before they are combined with other components.

Example: Testing a function that calculates the total price of an order.

### Advantages of Unit Testing

- Detects defects early.
- Makes debugging easier.
- Supports code changes.
- Improves component reliability.

### Integration Testing

Integration Testing verifies whether connected modules interact correctly.

It focuses on interfaces, data transfer, communication, and dependencies.

### Integration Testing Approaches

#### 1. Top-Down Integration

Testing begins with higher-level modules and proceeds downward.

Stubs may be used to simulate lower-level modules.

#### 2. Bottom-Up Integration

Testing begins with lower-level modules and proceeds upward.

Drivers may be used to simulate higher-level modules.

#### 3. Big-Bang Integration

Many modules are combined before testing.

Fault isolation can be difficult because several modules are integrated at once.

#### 4. Incremental Integration

Modules are combined and tested in smaller groups.

This makes it easier to isolate defects.

### Difference

Unit Testing checks individual components.

Integration Testing checks interactions between components.

---

## Q10. Explain the Software Testing Process

### Step 1: Requirement Analysis

Identify testable requirements and expected behaviour.

The testing team determines what needs to be verified.

### Step 2: Test Planning

Define:

- Testing scope
- Resources
- Schedule
- Responsibilities
- Testing strategy
- Risks

### Step 3: Test Case Design

Prepare test cases, test data, and expected results.

Test cases should cover normal inputs, invalid inputs, and important boundary conditions.

### Step 4: Test Environment Setup

Prepare the required hardware, software, tools, databases, and test data.

### Step 5: Test Execution

Execute test cases and record actual results.

Compare actual results with expected results.

### Step 6: Defect Reporting

Record failures and provide enough information to reproduce them.

### Step 7: Retesting

After defects are fixed, test the affected functionality again.

### Step 8: Regression Testing

Check that changes have not broken previously working functionality.

### Step 9: Test Closure

Summarize test results, unresolved defects, and remaining risks.

---

## Q11. Explain Basis Path Testing

### Definition

Basis Path Testing is a White Box Testing technique that identifies a set of linearly independent execution paths through a program.

It uses the control-flow graph and Cyclomatic Complexity to determine the number of independent paths in a basis set.

### Procedure

1. Draw the control-flow graph.
2. Count the nodes and edges.
3. Calculate Cyclomatic Complexity.
4. Identify independent paths.
5. Create test cases for those paths.
6. Execute the tests and verify the results.

### Cyclomatic Complexity Formula

For a single connected control-flow graph:

`V(G) = E - N + 2`

Where:

- `V(G)` = Cyclomatic Complexity
- `E` = Number of edges
- `N` = Number of nodes

An alternative formula using binary decision points is:

`V(G) = D + 1`

Where:

- `D` = Number of binary decision points

For a graph with `P` connected components, the general formula is:

`V(G) = E - N + 2P`

For one connected routine, `P = 1`, so:

`V(G) = E - N + 2`

### Example: checkDiscount()

```c
void checkDiscount(int amount) {
    if (amount > 2000) {
        print("Apply 25% Discount");
    } else {
        print("No Discount");
    }

    print("Transaction complete");
}
```

There is one binary decision.

Formula:

`V(G) = D + 1`

Substitution:

`V(G) = 1 + 1`

Final answer:

`V(G) = 2`

### Independent Paths

**Path 1:**

The condition `amount > 2000` is true.

The discount is applied, and the transaction completes.

**Path 2:**

The condition `amount > 2000` is false.

No discount is applied, and the transaction completes.

### Test Cases

- Input: `2500` — Discount is applied.
- Input: `1500` — No discount is applied.
- Input: `2000` — No discount is applied because the condition uses `>` rather than `>=`.

---

## Q12. Calculate Cyclomatic Complexity for swapIfGreater()

Consider the following code:

```c
void swapIfGreater(int a, int b) {
    if (a > b) {
        int temp = a;
        a = b;
        b = temp;
    }

    print("Final order");
}
```

There is one binary decision.

### Formula

`V(G) = D + 1`

### Substitution

`V(G) = 1 + 1`

### Final Answer

`V(G) = 2`

### Independent Paths

**Path 1:**

The condition `a > b` is true, so the values are swapped.

**Path 2:**

The condition `a > b` is false, so the values are not swapped.

### Test Cases

- Input `(8, 3)` — True path.
- Input `(3, 8)` — False path.
- Input `(5, 5)` — False path because the values are equal.

---

## Q13. Explain Boundary Value Analysis and Equivalence Class Partitioning

### Equivalence Class Partitioning

Equivalence Class Partitioning divides inputs into groups expected to behave similarly.

A representative value is selected from each group to reduce the number of test cases.

### Boundary Value Analysis

Boundary Value Analysis focuses on values at and around input limits.

Defects frequently occur at boundaries because of incorrect comparison operators or range handling.

### Example: Salary Validation

Assume the accepted salary range is Rs. 10,000 to Rs. 1,00,000, inclusive.

The valid condition is:

`10000 <= salary <= 100000`

### Equivalence Classes

**Invalid lower class:**

`salary < 10000`

Expected result: Reject.

**Valid class:**

`10000 <= salary <= 100000`

Expected result: Accept.

**Invalid upper class:**

`salary > 100000`

Expected result: Reject.

### Boundary Test Cases

1. Rs. 9,999 — Reject.
2. Rs. 10,000 — Accept.
3. Rs. 10,001 — Accept.
4. Rs. 99,999 — Accept.
5. Rs. 1,00,000 — Accept.
6. Rs. 1,00,001 — Reject.

These values assume integer salary inputs and inclusive endpoints.

### Advantages of BVA and ECP

- Reduce unnecessary test cases.
- Improve test coverage of important input conditions.
- Help detect range-validation errors.
- Make test design more systematic.

---

## Q14. Explain White Box Testing Techniques

### 1. Statement Coverage

Ensures that each executable statement is executed at least once.

### 2. Branch Coverage

Ensures that each decision outcome is tested.

For example, both the true and false branches of an `if` statement should be executed.

### 3. Condition Coverage

Ensures that each Boolean condition evaluates to both true and false where applicable.

### 4. Basis Path Testing

Identifies independent execution paths using Cyclomatic Complexity.

### 5. Loop Testing

Tests loops with zero, one, typical, and boundary numbers of iterations.

### 6. Data-Flow Testing

Examines how variables are defined and used.

### Conclusion

White Box Testing techniques help examine internal program logic and identify untested statements, branches, and paths.

Coverage measurements are useful, but high coverage alone does not prove that software is defect-free.

---

## Q15. Explain Software Testing Strategies

A common software testing strategy includes the following stages.

### 1. Unit Testing

Tests individual modules or functions.

### 2. Integration Testing

Tests communication between modules.

### 3. Validation Testing

Checks whether the software satisfies specified requirements.

### 4. System Testing

Tests the complete integrated system.

### 5. Acceptance Testing

Determines whether the software meets user or customer expectations.

### Other Testing Types

**Regression Testing:** Checks whether changes have broken existing functionality.

**Smoke Testing:** Performs a quick check of the build's major functions.

**Performance Testing:** Measures response time, throughput, and resource usage.

**Load Testing:** Evaluates behaviour under expected or high workloads.

**Stress Testing:** Examines behaviour beyond normal operating limits.

**Security Testing:** Checks security properties and weaknesses.

**Usability Testing:** Evaluates ease of use.

**Alpha Testing:** Evaluates software in a controlled environment.

**Beta Testing:** Collects feedback from selected users in realistic environments.

---

## Q16. Explain the Principles of Software Testing

### 1. Testing Shows the Presence of Defects

Testing can reveal defects, but it cannot prove that no defects exist.

### 2. Exhaustive Testing Is Impractical

Testing every possible input and execution path is generally impossible for non-trivial systems.

### 3. Early Testing

Testing should begin as early as possible in development.

Early defect detection generally reduces correction costs.

### 4. Defect Clustering

Defects often concentrate in a small number of modules.

These modules may require additional testing.

### 5. Pesticide Paradox

Repeating the same tests may eventually reveal fewer new defects.

Test cases should be reviewed and improved over time.

### 6. Context-Dependent Testing

Different software systems require different testing strategies.

Safety-critical software may need more rigorous testing than a small personal utility.

### 7. Absence-of-Errors Fallacy

Software can contain few known defects and still fail if it does not meet user needs.

---

# 4. MODULE 6 - RISK AND QUALITY MANAGEMENT

## Q17. Explain Software Risk and Its Types

### Definition

Software risk is an uncertain event or condition that may negatively affect project cost, schedule, scope, quality, or success.

### 1. Project Risk

Threatens project planning, staffing, budget, or schedule.

Example: A key developer leaves during an important phase.

### 2. Technical Risk

Threatens software quality or implementation.

Example: The selected technology cannot satisfy performance requirements.

### 3. Business Risk

Threatens the commercial success of the product.

Example: Customer requirements change significantly.

### 4. Operational Risk

Threatens normal operation or support.

Example: The production server becomes unavailable.

### 5. External Risk

Arises outside the direct control of the development team.

Example: A third-party service changes its interface.

> Different textbooks use different risk classifications. Follow the categories specified by your course.

### Risk Exposure Formula

`Risk Exposure = Probability x Impact`

Example:

Probability of delay:

`P = 0.30`

Estimated impact:

`I = Rs. 50,000`

Calculation:

`Risk Exposure = 0.30 x 50,000`

Final answer:

`Risk Exposure = Rs. 15,000`

This represents expected loss under the assumed probability and impact.

---

## Q18. Explain the RMMM Plan with an Example

### Definition

RMMM stands for:

- **R:** Risk Mitigation
- **M:** Monitoring
- **M:** Management

An RMMM plan identifies important risks, describes preventive actions, tracks warning signs, and specifies responses if risks occur.

### Main Components

1. Risk identification.
2. Probability and impact assessment.
3. Mitigation actions.
4. Monitoring indicators.
5. Contingency or management actions.
6. Assignment of responsibility.

### Example: Student Attendance System

#### Risk 1: Attendance Data Is Lost

**Mitigation:**

Schedule automatic backups and restrict database access.

**Monitoring:**

Check backup logs and perform periodic restore tests.

**Management:**

Restore the latest valid backup and reconcile records.

#### Risk 2: Faculty Do Not Adopt the System

**Mitigation:**

Provide training and a simple interface.

**Monitoring:**

Collect usage data and user feedback.

**Management:**

Provide additional training and temporary assistance.

#### Risk 3: Network Failure

**Mitigation:**

Prepare an approved offline attendance procedure.

**Monitoring:**

Monitor system availability and response time.

**Management:**

Record attendance through the fallback procedure and synchronize it later.

#### Risk 4: Incorrect Attendance Entries

**Mitigation:**

Validate inputs and maintain an audit trail.

**Monitoring:**

Review correction rates and unusual patterns.

**Management:**

Correct records through an authorized process.

### Conclusion

An RMMM plan helps a team identify risks early, reduce their likelihood or impact, monitor warning signs, and prepare appropriate responses.

---

## Q19. Explain Software Quality Assurance

### Definition

Software Quality Assurance (SQA) is a planned and systematic set of activities intended to provide confidence that software processes and products conform to requirements, standards, and procedures.

### Objectives of SQA

- Prevent defects.
- Improve software quality.
- Ensure compliance with standards.
- Improve maintainability and reliability.
- Increase customer satisfaction.
- Encourage continuous process improvement.

### SQA Process

#### Step 1: Quality Planning

Define quality goals, standards, responsibilities, and procedures.

#### Step 2: Standards Definition

Establish coding, documentation, testing, and review standards.

#### Step 3: Requirements Review

Check requirements for ambiguity, inconsistency, and incompleteness.

#### Step 4: Design Review

Identify design problems before implementation.

#### Step 5: Technical Reviews

Examine code, documents, and other work products.

#### Step 6: Testing Oversight

Check that testing activities are appropriate and documented.

#### Step 7: Defect Tracking

Record defects and track them to closure.

#### Step 8: Quality Measurement

Monitor relevant quality metrics.

#### Step 9: Process Improvement

Identify root causes and improve development practices.

#### Step 10: Quality Reporting

Communicate results and outstanding risks.

### SQA Versus Testing

Testing executes software to reveal failures.

SQA is broader and includes process standards, reviews, audits, quality measurement, and continuous improvement.

---

## Q20. Explain Software Configuration Management

### Definition

Software Configuration Management (SCM) is the process of identifying, organizing, and controlling changes to software artifacts throughout the software life cycle.

### Main SCM Activities

#### 1. Configuration Identification

Identify source code, requirements, documents, test cases, and builds that need control.

#### 2. Version Control

Track file history and maintain different versions.

#### 3. Change Control

Review and approve proposed changes before implementation.

#### 4. Configuration Status Accounting

Record and report the current state of configuration items.

#### 5. Configuration Auditing

Check that configuration items and records are complete and consistent.

#### 6. Build and Release Management

Produce and identify controlled software builds and releases.

### Version Control

Version Control records changes to files over time.

It supports:

- Change history.
- Branching and merging.
- Collaboration.
- Rollback.
- Identification of release versions.

### Change Control

A typical change-control sequence is:

`Change Request -> Impact Analysis -> Review and Approval -> Implementation -> Testing -> Record Update -> Release`

Change control reduces unauthorized or poorly understood changes.

### Benefits of SCM

- Improves traceability.
- Prevents version confusion.
- Supports team collaboration.
- Helps reproduce builds.
- Reduces the risk of losing work.
- Supports controlled releases.

---

## Q21. Differentiate Between FTR and Walkthrough

### Formal Technical Review (FTR)

- Usually follows a defined review procedure.
- Often uses a review leader or moderator.
- Uses preparation and review criteria.
- Records defects and follow-up actions.
- Checks technical correctness and compliance with standards.

### Walkthrough

- Usually less formal.
- Often led by the author.
- The author explains the work product step by step.
- Participants ask questions and identify possible defects.
- Helps improve understanding and collect feedback.

### Conclusion

FTR is generally more structured, while a walkthrough is commonly an author-guided review.

Terminology varies between textbooks and organizations, so follow the definition provided in your course notes.

---

## Q22. Explain Software Re-engineering

### Definition

Software Re-engineering is the examination and modification of existing software to improve its structure, maintainability, or other qualities while preserving or carefully evolving its functionality.

### Main Activities

#### 1. Inventory Analysis

Identify systems or components that require improvement.

#### 2. Document Restructuring

Improve outdated or incomplete documentation.

#### 3. Reverse Engineering

Analyse the existing system to recover design or requirements information.

#### 4. Code Restructuring

Improve code organization and readability.

#### 5. Data Restructuring

Improve the organization or format of data.

#### 6. Forward Engineering

Rebuild or evolve the software using the improved understanding.

### Advantages

- Extends the life of existing software.
- Improves maintainability.
- Reduces complexity.
- Preserves valuable functionality.
- May reduce the risk of complete replacement.

---

# 5. FORMULA REVISION SHEET

## 5.1 Cyclomatic Complexity

For one connected control-flow graph:

`V(G) = E - N + 2`

Where:

- `V(G)` = Cyclomatic Complexity
- `E` = Number of edges
- `N` = Number of nodes

Using binary decision points:

`V(G) = D + 1`

Where:

- `D` = Number of binary decision points

For a graph with `P` connected components:

`V(G) = E - N + 2P`

For one connected routine, `P = 1`, so:

`V(G) = E - N + 2`

### Example

If a program contains one binary decision:

`D = 1`

Therefore:

`V(G) = D + 1`

`V(G) = 1 + 1`

**Final Answer: `V(G) = 2`**

## 5.2 Risk Exposure

Formula:

`Risk Exposure = Probability x Impact`

If the probability is given as a percentage, convert it to a decimal before multiplying.

Example:

`30% = 0.30`

If the impact is Rs. 50,000:

`Risk Exposure = 0.30 x 50,000`

**Final Answer: Rs. 15,000**

## 5.3 Salary Validation Range

Assume the accepted salary range is Rs. 10,000 to Rs. 1,00,000, inclusive.

Valid condition:

`10000 <= salary <= 100000`

Boundary values:

- Rs. 9,999 — Reject.
- Rs. 10,000 — Accept.
- Rs. 10,001 — Accept.
- Rs. 99,999 — Accept.
- Rs. 1,00,000 — Accept.
- Rs. 1,00,001 — Reject.

---

# 6. LAST-MINUTE REVISION CHECKLIST

## Module 4 - Software Design

- [ ] Definition and types of cohesion.
- [ ] Definition and types of coupling.
- [ ] Cohesion versus coupling.
- [ ] Software design principles.
- [ ] Effective modular design.
- [ ] Architectural styles.
- [ ] Data-centered architecture.

## Module 5 - Software Testing

- [ ] Black Box versus White Box Testing.
- [ ] Alpha versus Beta Testing.
- [ ] Unit versus Integration Testing.
- [ ] Software testing process.
- [ ] Software testing strategies.
- [ ] Basis Path Testing.
- [ ] Cyclomatic Complexity formulas.
- [ ] Independent execution paths.
- [ ] Boundary Value Analysis.
- [ ] Equivalence Class Partitioning.
- [ ] White Box Testing techniques.
- [ ] Principles of software testing.

## Module 6 - Risk and Quality Management

- [ ] Software risk categories.
- [ ] Risk Exposure formula.
- [ ] RMMM plan and example.
- [ ] SQA definition and process.
- [ ] SCM activities.
- [ ] Version Control and Change Control.
- [ ] FTR versus Walkthrough.
- [ ] Software Re-engineering.

---

# 7. ANSWER-WRITING STRATEGY

## For a 2-Mark Question

1. Write a clear definition.
2. Add one or two important points.
3. Include a small example if useful.

## For a 7-Mark Question

1. Start with a definition.
2. Explain the main concepts under clear headings.
3. Use numbered lists for steps or types.
4. Include a comparison when relevant.
5. Add a suitable example.
6. Write formulas separately and substitute values step by step.
7. End with a brief conclusion.

## For Numerical Questions

Always show:

1. The formula.
2. The meaning of the variables.
3. The values substituted into the formula.
4. The calculation.
5. The final answer.
6. A short interpretation of the result.

---

**Final preparation tip:** Finish Priority 1 first, practise the Module 5 numerical questions, and then revise the remaining questions module by module.
