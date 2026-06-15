# Gym Class Activity - Feature Implementation Issues

## Overview
This document outlines the features identified in the Gym Class activity that should be implemented as issues for the Mergington High School Management System.

---

## Issue 1: Availability Tracking

**Title:** Display and dynamically update available spots for activities

**Description:**
Implement real-time availability tracking for activities showing how many spots remain based on the maximum capacity and current participants.

**Acceptance Criteria:**
- [ ] Display available spots count on each activity card
- [ ] Calculate availability as: `max_participants - current_participants`
- [ ] Update availability dynamically when users sign up or unregister
- [ ] Show "Full" status when no spots remain

**Related Code:**
- Backend: `activities` dict in `app.py` with `max_participants` and `participants` fields
- Frontend: Display in `activity-card` div in `index.html`

---

## Issue 2: Participant Management

**Title:** Implement participant list viewing and removal functionality

**Description:**
Provide users the ability to view all participants enrolled in an activity and remove them with a delete button.

**Acceptance Criteria:**
- [ ] Display participant email addresses in a list format
- [ ] Add delete (❌) button next to each participant
- [ ] Implement click handler for delete button
- [ ] Call `/activities/{activity_name}/unregister` DELETE endpoint
- [ ] Display success/error message after deletion
- [ ] Refresh activity list after successful removal

**Related Code:**
- Backend: `@app.delete("/activities/{activity_name}/unregister")` endpoint
- Frontend: `handleUnregister()` function in `app.js`

---

## Issue 3: Student Sign-Up Integration

**Title:** Enable students to sign up for activities

**Description:**
Implement a complete sign-up workflow allowing students to select an activity and register with their email address.

**Acceptance Criteria:**
- [ ] Create sign-up form with email input and activity dropdown
- [ ] Populate dropdown with available activities
- [ ] Submit form via POST to `/activities/{activity_name}/signup`
- [ ] Validate student email is required
- [ ] Prevent duplicate sign-ups
- [ ] Clear form after successful submission
- [ ] Display confirmation message

**Related Code:**
- Backend: `@app.post("/activities/{activity_name}/signup")` endpoint with validation
- Frontend: `signup-form` form and submit handler in `app.js`

---

## Issue 4: Data Persistence

**Title:** Maintain participant data across API calls

**Description:**
Ensure that participant information is reliably stored and retrieved, with changes persisting across multiple requests.

**Acceptance Criteria:**
- [ ] Participant list updates persist after sign-up
- [ ] Participant removal persists after unregister
- [ ] API returns updated activity data after modifications
- [ ] No data loss on concurrent requests (consider future database implementation)

**Related Code:**
- Backend: In-memory `activities` dictionary in `app.py`
- Note: Currently in-memory; should consider database migration for production

---

## Issue 5: User Feedback System

**Title:** Display success and error messages for user actions

**Description:**
Implement a notification system that provides clear feedback to users about the success or failure of their actions.

**Acceptance Criteria:**
- [ ] Display success messages in green for successful operations
- [ ] Display error messages in red for failed operations
- [ ] Show custom error details from API responses
- [ ] Auto-hide notifications after 5 seconds
- [ ] Messages appear in consistent location (message div)

**Related Code:**
- Frontend: `messageDiv` in `index.html` and message handling in `app.js`
- Styling: `message`, `success`, `error` classes in `styles.css`

---

## Summary

These five features work together to create a complete activity management system where:
1. Students can browse available activities with up-to-date availability info
2. Students can sign up for activities they're interested in
3. Administrators/users can view participants and manage enrollment
4. The system provides clear feedback on all actions
5. Data changes are reliably persisted

**Estimated Effort:** Medium (already implemented, but good for documentation and future enhancements)

**Priority:** Medium (core functionality for activity management)
