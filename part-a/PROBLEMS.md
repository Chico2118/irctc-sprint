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

- Tatkal passengers
- Emergency travelers
- Daily commuters
- Booking agents

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

## Problem 2: Search Filters Do Not Work Reliably [Given]

### What is broken

The train search results page provides filters for quota type, class, availability, and departure time. These filters frequently either do not apply correctly, reset when the page refreshes or when users navigate back, or show trains that do not fully match the selected filter criteria. This forces users to repeatedly reapply filters and manually verify search results.

### Affected users

- Passengers comparing multiple train options
- Users booking tickets during peak travel seasons
- Senior citizens and less tech-savvy users
- Daily commuters searching for specific train timings
- Users with limited internet bandwidth who want faster decision-making

Since train search is the entry point for almost every booking journey, this issue potentially affects a large percentage of IRCTC users.

### Frequency

- Observed throughout the day
- Occurs whenever users perform train searches and refine results
- More noticeable when users repeatedly change filters or navigate between search results and train details

### Current Flow — Step by Step

1. User opens IRCTC and logs into their account.
2. User enters source station and destination station.
3. User selects journey date and clicks Search.
4. The train results page loads with multiple train options.
5. User applies filters such as Sleeper Class, Available Seats Only, and Morning Departure.
6. The results appear to update according to the selected filters.
7. User opens a train to view availability, fare details, or schedule information.
8. User clicks the browser Back button or returns to the search results page.
9. Previously selected filters are reset or applied inconsistently.
10. Some trains shown in the results no longer match the originally selected criteria.
11. User must manually reapply filters.
12. User repeats the search and verification process before making a booking decision.

### Where Exactly It Breaks

**Step 8–10.**

The system fails to consistently preserve filter state when users navigate away from the results page and return. As a result:

- Selected filters may disappear.
- Search results may refresh unexpectedly.
- Users may see trains that do not align with their chosen criteria.
- Additional effort is required to verify train options again.

This creates friction during the train discovery process and increases the time required to complete a booking.

### User Impact

- Increased search time
- Reduced trust in search results
- Higher likelihood of selecting an incorrect train
- Frustration caused by repetitive filtering actions
- Poor user experience for passengers comparing multiple options

### Screenshot

`assets/screenshots/problem2-filters.png`

### Severity

**Medium–High**

The issue does not completely block bookings, but it affects the core train discovery experience used by nearly every passenger before ticket purchase.

---

## Problem 3: Seat Selection Resets [Given]

### What is broken

Passengers can select a preferred berth (Lower Berth, Upper Berth, Side Lower, etc.) during the booking process, but this preference is not always preserved consistently across booking screens. In some cases, the selected preference resets, disappears, or is not clearly reflected in subsequent steps, creating uncertainty about whether the request has been recorded.

### Affected users

- Senior citizens who prefer lower berths
- Families traveling together
- Female passengers traveling alone
- Long-distance travelers
- Passengers with mobility concerns

These users rely heavily on berth preferences for comfort, accessibility, and safety.

### Frequency

- Intermittent but recurring
- Reported more frequently on mobile browsers and slower network connections
- Occurs during the passenger details to review stage of booking

### Current Flow — Step by Step

1. User searches for a train.
2. User selects a train and quota.
3. User clicks Book Now.
4. Passenger Details page opens.
5. User enters passenger information.
6. User selects a berth preference such as Lower Berth.
7. User reviews entered details.
8. User clicks Continue or Proceed.
9. Review or confirmation page loads.
10. Previously selected berth preference is missing, changed, or not clearly displayed.
11. User becomes unsure whether the preference was saved.
12. User proceeds with uncertainty or goes back to verify details.

### Where Exactly It Breaks

**Step 9–10.**

The system fails to consistently communicate that the selected berth preference has been retained. Either the preference is reset, not displayed, or the UI provides insufficient confirmation that the selection was saved.

### User Impact

- Reduced confidence in the booking process
- Anxiety about berth allocation
- Increased need to recheck booking details
- Poor experience for passengers with specific seating requirements
- Potential dissatisfaction during actual travel if expectations are not met

### Screenshot

`assets/screenshots/problem3-seat-selection.png`

### Severity

**Medium**

The issue does not prevent ticket booking but directly affects user trust and perceived reliability of the booking experience.

---
