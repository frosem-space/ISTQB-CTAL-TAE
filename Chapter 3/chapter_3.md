<p align="center">
  <a href="https://www.istqb.org/certifications/certified-tester-advanced-level-test-automation-engineering-ctal-tae-v2-0/">
    <img src="https://www.istqb.org/wp-content/uploads/2024/10/ISTQB_CT_TAE_v2.0-1024x940-1.png.avif" width="200" alt="ISTQB CTAL-TAE Logo"/>
  </a>
</p>

# Chapter 3: Test Automation Architecture

| K-Level | Question Distribution | Learning Objective | Number of Questions | Suggested Points |
|-|-|-|-|-|
| K2 | TAE-3.1.1 | Explain the major capabilities in a test automation architecture | 1 | 1 |
| K2| TAE-3.1.2 | Explain how to design a test automation solution | 1 | 1 |
| K3 | TAE-3.1.3 | Apply layering of test automation frameworks | 1 | 2 |
| K3 | TAE-3.1.4 | Apply different approaches for automating test cases | 2 | 2 |
| K3 | TAE-3.1.5 | Apply design principles and design patterns in test automation | 1 | 2 |

**Total Questions for Chapter 3: 5**  
K2 = 2  
K3 = 8  
Total Points: 10  

---

## 3.1 Design Concepts Leveraged in Test Automation

### 3.1.1 Explain the Major Capabilities in a Test Automation Architecture

The **Generic Test Automation Architecture (gTAA)** defines how test automation connects to:

| gTAA Interfaces | Description |
| - | - |
| The **SUT** | Describes the connection between the SUT and the **TAF** (Test Automation Framework). |
| **Project management** | Describes the test automation development progress. |
| **Test management** | Describes the mapping of test case definitions and automated test cases. |
| **Configuration management** | Describes the CI/CD pipelines, environments and testware. |

**Capabilities to cover when designing a test automation architecture:**
- **Test generation**:  
  Optional. support the automated design of test cases using model-based testing tools or test model (**CT-MBT**, [Section 3.2.1](https://www.istqb.org/wp-content/uploads/2024/11/ISTQB_CT-MBT_-_Syllabus_Version_v1.1.pdf#page=30)).

- **Test definition**:  
  Supports the definition and implementation of test cases and/or test suites, high and low-level test cases defined independently of SUT/tools.

- **Test execution**:  
  Supports test execution and test logging. Run the selected tests, logging and test reporting.

- **Test adaptation**:  
  Adapts tests for various SUT interfaces (APIs, protocols, services).

---

### 3.1.2 Explain How to Design a Test Automation Solution

A **Test Automation Solution (TAS)** includes:
- Understanding functional, non-functional, and technical SUT requirements.

- Selection of commercial/open-source tools and custom adaptors specific for the SUT.

The **Test Automation Architecture (TAA)** defines the TAS’s technical design:
- Select automation tools/libraries.

- Develop plugins/components.

- Define connectivity or interfaces (firewalls, DBs, URLs, mocks/stubs, queues, protocols).

- Integrate with test/defect management tools.

- Set up version control system (Git) and repositories (GitHub, GitLab, etc).

---

### 3.1.3 Apply Layering of Test Automation Frameworks

The **Test Automation Framework (TAF)** is the base of the TAS. It contains **Test harness (runner)**, test libraries, test scripts and test suites.

**TAF Layers** defines classes with similar purposes, by introducing a layer for each single purpose, the design can become complicated, it is recommended to keep the number of
TAF layers low for clarity and maintenance.

| Layer | Purpose |
|--------|---------|
| **Test scripts** | Test case repository and test suite annotations, calls business logic services (user flows, API calls). No direct calls to core libs. |
| **Business logic** | Used to set up the TAF to run against the SUT and the additional configurations, SUT-dependent libs. Libs inherits core libs or use the facades.  |
| **Core libraries** | SUT-independent reusable code for any type of projects that shares the same development stack. |

**Scaling test automation:**  
Core libraries can be reused in several TAFs across projects.

---

### 3.1.4 Apply Different Approaches for Automating Test Cases

Different methods can be used to automate test cases, each with pros and cons.

- **TDD/BDD** are development methods but result in automated tests.

- **No-code/low-code tools** (capture/playback) are easy to start but hard to scale.

- **Structured scripting, DDT, and KDT** improve reusability but need more setup.

- **BDD** requires team collaboration to work well.

---

| Approach               | Description | Pros | Cons |
|------------------------|------------|------|------|
| **Capture/Playback** | Records manual interactions with the system (SUT) to create test scripts. | <li>Easy to setup and use.<li>No coding needed (no-code/low-code tools). | <li>Hard to maintain. <li>Needs SUT available during capture. <li>Works only for small, stable systems. |
| **Linear Scripting** | Uses simple scripts, often modified from recorded tests. | <li>Easier to modify than capture/playback. <li>Simple setup. | <li>Still hard to maintain. <li>Needs SUT available. <li>Requires basic programming. |
| **Structured Scripting** | Uses reusable test libraries and steps. | <li>Easier to maintain and scale. <li>Separates business logic from scripts. | <li>Needs programming skills. <li>Takes time to set up. |
| **Test-Driven Development (TDD)** | Write tests before coding (Red → Green → Refactor). | <li>Better code quality and test coverage. <li>Reduces defects early. <li>Improves team communication. | <li>Takes time to learn. <li>False confidence if not done properly. |
| **Data-Driven Testing (DDT)** | Uses external data files (e.g., CSV) to run the same test with different inputs. | <li>Easy to add new tests via data. <li>Reduces test creation effort. <li>Less technical dependency for testers. | <li>Needs good test data management. |
| **Keyword-Driven Testing (KDT)** | Uses keywords (user actions) with test data in tables. | <li>Non-technical users like business analysts can help create tests. <li>Can also be used for manual testing. | <li>Complex to set up and maintain. <li>Huge effort for smaller systems. |
| **Behavior-Driven Development (BDD)** | Uses natural language (Given/When/Then) for test cases stored in feature files. | <li>Better team communication. <li>Tests cover specifications directly. <li>Works for multiple test levels. | <li>Still needs extra test cases (edge cases). <li>Hard to maintain if steps are too complex. <li>Overly complex test steps will turn debugging into a difficult and costly activity. |


---

### 3.1.5 Apply Design Principles and Design Patterns in Test Automation

Test automation is like software development, so good design principles and patterns help make tests more maintainable and scalable.  

### **Object-Oriented Programming (OOP) Principles**  

| Principle      | Description |
|---------------|------------|
| **Encapsulation** | Keeps data and methods together, hiding internal details. |
| **Abstraction**  | Shows only what’s needed, hiding complexity. |
| **Inheritance**  | Lets classes reuse properties and methods from other classes. |
| **Polymorphism** | Allows methods to work in different ways based on context. |

### SOLID Principles

| Principle | Description | Benefit |
|-----------|-------------|-------------|
| **Single Responsibility** | A class should have only one job. | Easier to maintain and modify. |
| **Open-Closed** | Code should be open for extension but closed for modification. | Reduces risk when adding new features. |
| **Liskov Substitution** | Subclasses should work where parent classes are used. | Prevents unexpected behavior. |
| **Interface Segregation** | Use small, specific interfaces instead of big general ones. | Avoids unnecessary dependencies. |
| **Dependency Inversion** | Depend on abstractions, not concrete implementations. | Makes code more flexible and testable. |

### Important Design Patterns for Test Automation

| Pattern | Description | Use in Test Automation |
|---------|-------------|-------------------------|
| **Facade** | Hides complex systems behind a simple interface. | Simplifies test case creation by exposing only needed functions. |
| **Singleton** | Ensures only one instance of a class exists. | Often used for SUT communication drivers. |
| **Page Object Model (POM)** | Creates classes representing application pages. | When UI changes, only update locators in one place. |
| **Flow Model** | Adds another layer over POM for user actions. | Improves reusability of test steps across scripts. |

---

## Summary of Key Concepts

- A test automation architecture defines connections, capabilities, and structure.

- A solid TAS aligns with SUT requirements, tools, and infrastructure needs.

- Layering frameworks and reusing core libraries improves scalability.

- Choose test automation approaches based on scope, maintenance needs, and team skill.

- Apply design principles and patterns to build reliable, maintainable, and scalable automation.

---
> ✅ **Good automation architecture is planned, layered, and designed to evolve with the product.**
---
> ⚠️ **Avoid over-complicating the framework or not using patterns can lead to difficult the success of the TAS.**
---
