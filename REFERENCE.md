# Module 01: Reading JIRA Tickets 🎫

> Every task you'll do in this simulator starts with a **TICKET.md** file.
> This is your assignment — like a homework sheet, but for a real company.
> Learning to read tickets is THE #1 skill that separates good interns from lost ones.

---

## What Is a JIRA Ticket?

In real companies, work is tracked in a tool called **JIRA** (or Linear, Asana, etc.).
Each piece of work — bug fix, new feature, or improvement — gets a **ticket**.

A ticket tells you:
- **What** needs to be done
- **Why** it matters
- **How** to verify you did it right
- **Who** asked for it and **when** it's due

---

## Anatomy of a Ticket

Here's a real ticket from Week 1. Let's break down every part:

```
# PLATFORM-2835: Implement REST API rate limiter middleware

Status: In Progress · Priority: High
Sprint: Sprint 23 · Story Points: 5
Reporter: Kavitha Rajan (API Gateway Lead) · Assignee: You (Intern)
Created: 2026-02-10 · Due: End of sprint (Friday)
Labels: backend, api-gateway, nodejs, middleware
Epic: PLATFORM-2810 (API Gateway Hardening)
```

### Breaking it down:

| Field | What It Means | Why You Care |
|-------|---------------|--------------|
| **PLATFORM-2835** | Unique ticket ID | Reference this in PRs and Slack messages |
| **Status: In Progress** | You're actively working on it | Others know not to pick it up |
| **Priority: High** | How urgent this is | High = do it this sprint, don't delay |
| **Story Points: 5** | Estimated effort (1=tiny, 13=huge) | 5 = a solid day of work |
| **Reporter** | Who created the ticket | Ask THEM if requirements are unclear |
| **Labels** | Categories | Tells you the language, area, and type |
| **Epic** | Parent project | Shows how your work fits the bigger picture |
| **Due: End of sprint** | Your deadline | Missing this = bad KPI |

---

## The Sections You MUST Read

### 1. Description
This tells you the **context** and **backstory**:
- What already exists
- What's broken or missing
- Who worked on it before (their code may have bugs!)

**KEY PHRASE TO WATCH FOR:**
> "The previous intern started this work but..."

This means you're inheriting buggy code. Don't assume it works!

### 2. Requirements
These are the **rules** your solution must follow. Treat them as LAW.
- If it says "Thread-safe" → you MUST use locks
- If it says "Return 429" → the exact status code matters
- Don't add features that aren't listed here

### 3. Acceptance Criteria
These are **checkboxes** that define "done." Your work is not complete until
ALL boxes can be checked. These map directly to test cases.

```
- [ ] Requests under the limit pass through successfully
- [ ] Requests over the limit get 429 response
- [ ] Retry-After header contains correct remaining seconds
```

**Pro tip:** Read these BEFORE looking at the code. They tell you what
the tests will check.

### 4. Design Notes
Points you to other files with context:
- `docs/DESIGN.md` — Architecture decisions (why things are built this way)
- `.context/pr_comments.md` — Previous code review feedback (hints about known issues)

**Always read these.** They often contain clues about where the bugs are.

---

## How to Read a Ticket — The 5-Minute Method

1. **Read the title** — What's the feature/bug about? (30 seconds)
2. **Check priority and due date** — Is this urgent? (10 seconds)
3. **Read the description** — What's the backstory? (1 minute)
4. **Study the requirements** — What are the rules? (2 minutes)
5. **Read acceptance criteria** — What does "done" look like? (1 minute)
6. **Check design notes** — Any extra context? (30 seconds)

**Only THEN** open the code.

---

## Common Ticket Mistakes Interns Make

| Mistake | What Happens | How to Avoid |
|---------|-------------|--------------|
| Jumping to code before reading the ticket | You fix the wrong thing | Always read the FULL ticket first |
| Ignoring acceptance criteria | Your "fix" doesn't pass tests | Check each criterion like a checklist |
| Not reading `.context/` files | You miss important clues | Always check PR comments |
| Adding extra features | Code review rejects your PR | Only do what the ticket says |
| Ignoring the priority field | You work on a P3 while a P0 is burning | Check priority first |

---

## Practice

Open `Week-1/Task-3/TICKET.md` and answer these questions in your head:
1. What's the ticket ID?
2. Who reported it?
3. What language is this task in? (check the labels)
4. What does the acceptance criteria say about empty queues?
5. Where should you look for the previous intern's code review?

If you can answer all 5 — you know how to read a ticket! ✅
