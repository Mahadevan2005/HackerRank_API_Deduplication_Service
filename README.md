# Transaction Deduplication API
**Problem Statement Submission | Technical Content Engineer Intern**

---

## Overview

This is the problem statement for HackerRank's content library addressing **API idempotency**, a critical challenge every backend developer encounters when building payment systems, microservices, or REST APIs.

**Type:** Spring Boot Development Challenge | **Difficulty:** Medium | **Duration:** 60 minutes

---

## Repository Structure

```
├── README.md                    # Submission overview
├── ProblemStatement.md          # Candidate-facing problem
└── TestCaseDocumentation.md     # Test specification for backend evaluation
```

---

## Design Criteria

I designed this problem with three core principles:

**Clarity** - HackerRank-standard format, explicit requirements, no cultural bias  
**Innovativeness** - Real-world idempotency challenge every backend developer faces  
**Comprehensive Testing** - 10 test cases covering functional, boundary, concurrency, validation, and performance scenarios

---

## Content Engineering Approach

Built with three stakeholders in mind:

- **Candidates:** Clear evaluation testing production-relevant skills
- **Evaluators:** Standardized format enabling consistent grading  
- **HackerRank:** Ready-to-deploy content fitting seamlessly into the library

**Key Strengths:**
- Tests design thinking, not just coding ability
- Multi-dimensional evaluation (API design, concurrency, memory management)
- Scalable documentation style replicable across problem sets

---

## Test Coverage

| Category | Cases | Coverage |
|----------|-------|----------|
| Functional | 4 | Core deduplication logic, time windows |
| Boundary | 1 | Exact 5-minute edge case |
| Concurrency | 1 | Thread safety, race conditions |
| Validation | 3 | Input sanitization, business rules |
| Performance | 1 | Memory Management |

---

## Why This Works

**Junior Devs:** Tests REST API fundamentals and time-based logic  
**Mid-Level Devs:** Evaluates design trade-offs and synchronization strategy  
**Senior Devs:** Assesses production thinking and maintainable system design

**Real-World Relevance:** Payment gateways (Stripe, Razorpay, PayPal) all implement this pattern

---

## Growth Potential

**Variations:** Redis-based deduplication, rate limiting, webhook idempotency  
**Difficulty Levels:** Easy (basic), Medium (current), Hard (distributed systems)  
**Extensions:** Redis, rate limiting, observability

---

## Quality Assurance

- **Bias-free:** Culturally neutral, globally understandable
- **Test-ready:** Executable specifications with clear pass/fail criteria
- **Production-ready:** Can be deployed to content library

---
- *Refer `ProblemStatement.md` for Question statement.*
- *Refer `TestCaseDocumentation.md` for Tests coverage.*