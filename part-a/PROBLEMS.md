# IRCTC Problem Discovery — Part A

## Summary

- Total problems documented: 6
- Given problems: 3
- Self-discovered problems: 3
- Platform explored: irctc.co.in
- Devices used: Desktop Chrome and Mobile Chrome
- Exploration Date: June 2026

---


## Problem 1: Tatkal Booking Crashes at 10:00 AM [Given]

### What is broken

The Tatkal booking flow becomes unstable during peak demand hours. Users encounter loading loops, booking failures, and session expirations without meaningful feedback.

### Affected users

* Tatkal passengers
* Emergency travelers
* Daily commuters
* Booking agents

### Frequency

Daily at 10:00 AM (AC Tatkal) and 11:00 AM (Non-AC Tatkal).

### Current flow

1. User opens IRCTC before quota opens.
2. User logs in.
3. User searches train.
4. User selects Tatkal quota.
5. User enters passenger details.
6. User waits for booking window.
7. User clicks Book.
8. Loading screen appears.
9. Server slows down.
10. Request fails or session expires.
11. User refreshes.
12. Tatkal quota becomes unavailable.

### Where exactly it breaks

Steps 8–10. High traffic causes backend congestion and users receive insufficient status information.

### Screenshot

assets/screenshots/problem1-tatkal.png

---


