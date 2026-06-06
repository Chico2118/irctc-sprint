# Impact vs Effort Matrix

## The Matrix

|                 | Low Effort                                               | High Effort                                                   |
| --------------- | -------------------------------------------------------- | ------------------------------------------------------------- |
| **High Impact** | Persistent Smart Filters, Multi-Step Mobile Booking Form | Tatkal Virtual Queue System                                   |
| **Low Impact**  | Berth Preference Lock System, Smart Captcha Recovery     | PNR Status Explanation Panel, Waitlist Confirmation Predictor |

---

## How I Scored Each Dimension

### Impact Scoring (1–5)

I scored Impact based on:

- Number of users affected
- Whether the issue impacts the core booking flow
- Frequency of occurrence
- Severity of user frustration

### Effort Scoring (1–5)

I scored Effort based on:

- Number of system components affected
- Backend complexity
- API changes required
- New infrastructure requirements
- Risk of breaking existing flows

---

## Placement Justifications

### Tatkal Virtual Queue System — High Impact / High Effort

This problem affects thousands of users every day during Tatkal booking hours and directly impacts ticket purchases. The solution requires frontend changes, backend queue infrastructure, real-time updates, and Redis integration. Because of its user impact and implementation complexity, it belongs in the High Impact / High Effort quadrant.

### Persistent Smart Filters — High Impact / Low Effort

Search is used by nearly every IRCTC user, making this issue highly visible. The fix mainly requires session persistence and frontend state management. Since implementation is relatively simple while improving a critical user journey, it is a Quick Win.

### Berth Preference Lock System — Low Impact / Low Effort

This issue affects only users with berth preferences and does not prevent booking completion. The solution requires only minor UI and API updates. It delivers value but is not a top-priority investment.

### Smart Captcha Recovery — Low Impact / Low Effort

The issue impacts authentication but not the booking process itself. The implementation is relatively straightforward and can be handled within the existing login system. It improves usability without significant engineering effort.

### PNR Status Explanation Panel — Low Impact / High Effort

While it improves understanding for passengers, it does not directly impact bookings. Building explanation systems, multilingual support, and prediction logic increases complexity. Therefore it falls into Low Impact / High Effort.

### Multi-Step Mobile Booking Form — High Impact / Low Effort

A large percentage of users book tickets through mobile devices. Splitting a long form into smaller steps significantly improves completion rates and user experience. The required changes are mostly frontend-focused, making it a strong Quick Win.

---

## Recommended Sprint Order

1. Persistent Smart Filters — Quick win with immediate usability improvements.
2. Multi-Step Mobile Booking Form — Improves completion rate for a large user base.
3. Smart Captcha Recovery — Low effort and improves authentication experience.
4. Berth Preference Lock System — Enhances trust in booking flow.
5. Tatkal Virtual Queue System — High-impact strategic project requiring more engineering effort.
6. PNR Status Explanation Panel — Valuable enhancement after core booking issues are addressed.

---

