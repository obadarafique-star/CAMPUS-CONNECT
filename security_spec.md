# Security Specification - CampusConnect

## Data Invariants
1. A Task must belong to a valid Program managed by a user with role='manager'.
2. A Submission must reference a valid Task and a User with role='ambassador'.
3. Points can only be updated when a submission is approved.
4. Managers can only manage their own programs and tasks/submissions within them.
5. Ambassadors can only read tasks for programs they are part of and can only read/write their own submissions.

## The Dirty Dozen Payloads (Rejection Targets)

1. **Identity Spoofing**: Attempt to create a user profile with `role: "manager"` as an unauthorized user.
2. **Resource Poisoning**: Create a Program with a 1MB description string.
3. **Orphaned Task**: Create a Task with a random `programId` that doesn't exist.
4. **Shadow Write**: Update a Submission status from `pending` to `approved` as an ambassador.
5. **Self-Assigned Points**: Update `users/{userId}/points` directly from the client.
6. **Cross-Program Access**: A manager attempting to read submissions from a program they don't own.
7. **Bypassing Validation**: Submitting a task with a negative point value.
8. **Spam Submissions**: An ambassador sending 100 submissions for the same task in 1 second.
9. **Role Escalation**: An ambassador attempting to update their own role to 'manager'.
10. **Ghost Field**: Adding `isVerified: true` to a user document.
11. **Spoofed Ownership**: Creating a program and setting `managerId` to another user's UID.
12. **Deadline Bypass**: Submitting a task after the `deadline` has passed.

## Firestore Rules Draft logic

- `isValidUser`: Checks keys, role, points=0 on create, immutable role on update.
- `isValidProgram`: Checks keys, managerId matches auth.uid.
- `isValidTask`: Checks keys, points > 0.
- `isValidSubmission`: Checks keys, ambassadorId matches auth.uid, status='pending' on create.

(This spec will guide the production rules)
