# PLATFORM-4100: Fix Session Timeout Not Extending on Activity

**Status:** In Progress · **Priority:** Medium
**Sprint:** Sprint 25 · **Story Points:** 3
**Reporter:** Ananya Rao (QA) · **Assignee:** You (Intern)
**Created:** 2026-02-20 · **Due:** End of sprint (Friday)
**Labels:** `backend`, `auth`, `session`, `python`
**Epic:** PLATFORM-4000 (Auth Service v4)
**Task Type:** Bug Fix

---

## Description

Users are getting logged out after 30 minutes even when actively using the app. The session
timeout should reset every time the user makes an API call, but it's not resetting.

Senior dev Vikram started debugging but got pulled to another incident. He left notes in
`.context/pr_comments.md`.

## Acceptance Criteria

- [ ] Session timeout resets on every authenticated API call
- [ ] Inactive sessions still expire after 30 minutes
- [ ] Session extension is logged for audit trail
- [ ] All unit tests pass

## Design Notes

See `docs/DESIGN.md` for the session architecture.
See `.context/meeting_notes.md` for sprint planning context.

---

### Slack Thread — #backend-bugs — Feb 20, 2026

**@ananya.rao** 2:30 PM:
> Users are complaining about being logged out during active sessions.
> I tested it — made a request at minute 25, still got logged out at minute 30.

**@vikram.shah** 2:45 PM:
> I think the `extend_session()` method is being called but not actually
> updating the expiry timestamp. Check the session store.
