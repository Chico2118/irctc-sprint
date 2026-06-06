# Feature Spec 1: Tatkal Virtual Queue System

### Problem Statement

Part A identified that Tatkal booking frequently crashes during peak demand at 10 AM and 11 AM. Users experience loading loops, booking failures, and session expirations, causing them to lose booking opportunities.

### Current State (from Part A)

The failure occurs between booking submission and server processing. Thousands of users hit the same endpoint simultaneously, creating congestion and poor feedback.

### Proposed Solution

Instead of everyone competing at once, users enter a virtual queue before booking opens. The system displays queue position, estimated wait time, and booking readiness.

### Proposed User Flow

1. User selects Tatkal train.
2. User enters queue before booking opens.
3. System assigns queue number.
4. User sees live queue position.
5. User receives turn notification.
6. User gets 90 seconds to complete booking.
7. Booking proceeds normally.

### Technical Implementation Plan

**System Components Affected**

- Frontend
- Booking API
- Queue Service
- Notification Service

**New Data Requirements**

- Queue ID
- User ID
- Queue Position
- Entry Timestamp

**API Changes**

- POST /queue/join
- GET /queue/status
- POST /queue/complete

**Frontend Changes**

- Queue Position Card
- Countdown Timer
- Progress Bar

**Third Party Services**

- Redis for queue management

### Success Metrics

- Reduce booking failures by 60%
- Increase Tatkal completion rate
- Reduce refresh attempts

### Edge Cases

- User closes browser
- Network disconnect
- Queue timeout
- Duplicate sessions

---

# Feature Spec 2: Persistent Smart Filters

### Problem Statement

Part A identified that search filters such as Sleeper Class, Available Seats Only, and Departure Time frequently reset when users navigate away from search results. This forces users to repeatedly reapply filters and slows train discovery.

### Current State (from Part A)

The failure occurs when users open train details and return to search results. Previously selected filters are lost or applied inconsistently.

### Proposed Solution

The system automatically saves active filters during a search session. When users return to the search page, all selected filters remain applied and visible.

### Proposed User Flow

1. User searches trains.
2. User applies filters.
3. Filters are automatically saved.
4. User opens train details.
5. User returns to search results.
6. Previously selected filters remain active.
7. User continues browsing without reapplying filters.

### Technical Implementation Plan

**System Components Affected**
- Search Frontend
- Search API
- Session Storage

**New Data Requirements**
- Filter Preferences
- Session ID

**API Changes**
- GET /search/preferences
- POST /search/preferences

**Frontend Changes**
- Filter Persistence
- Saved Filter Chips
- Restore Search State

**Third Party Services**
- None

### Success Metrics

- Reduce filter reapplication rate by 80%
- Improve train search completion rate
- Reduce search abandonment

### Edge Cases

- Browser refresh
- Session expiration
- Shared devices

### Wireframe

![Persistent Filters](../assets/wireframes/filters-persist.png)

