# Impact vs Effort Prioritisation Matrix

## Overview

The six proposed solutions were evaluated based on:

### Impact

How much value the solution delivers to users and IRCTC.

### Effort

Estimated engineering, infrastructure, and operational effort required for implementation.

---

# Matrix

| Feature                            | Impact    | Effort | Quadrant      |
| ---------------------------------- | --------- | ------ | ------------- |
| Persistent Smart Filters           | High      | Low    | Quick Win     |
| Auto Availability Loader           | High      | Low    | Quick Win     |
| Guided Concession Assistant        | Medium    | Low    | Fill-In       |
| Accessibility Recovery Suggestions | Medium    | Medium | Fill-In       |
| Seat Preference Lock System        | High      | Medium | Major Project |
| Tatkal Virtual Queue System        | Very High | High   | Major Project |

---

# Quadrant 1 — Quick Wins

## 1. Persistent Smart Filters

### Why it belongs here

High impact because almost every train-search user interacts with filters.

Low effort because the solution primarily involves frontend state management and session persistence.

### Expected Benefits

* Faster search experience
* Reduced user frustration
* Improved search completion rate

---

## 2. Auto Availability Loader

### Why it belongs here

High impact because users constantly check availability before booking.

Low effort because availability data already exists and only requires improved presentation and bulk loading.

### Expected Benefits

* Reduced clicks
* Faster booking decisions
* Improved usability

---

# Quadrant 2 — Major Projects

## 3. Tatkal Virtual Queue System

### Why it belongs here

Extremely high impact because it addresses one of IRCTC's most visible and long-standing problems.

High effort because it requires:

* Queue infrastructure
* Real-time updates
* Session management
* Backend architecture changes

### Expected Benefits

* Reduced crashes
* Higher booking success rate
* Better user trust

---

## 4. Seat Preference Lock System

### Why it belongs here

High impact for families, senior citizens, and passengers requiring specific berths.

Medium-to-high effort because seat inventory management must change.

### Expected Benefits

* Reduced booking errors
* Better seat assignment reliability
* Improved passenger satisfaction

---

# Quadrant 3 — Fill-Ins

## 5. Guided Concession Assistant

### Why it belongs here

Moderate impact for a specific user segment.

Low effort because most information already exists and only needs better presentation.

### Expected Benefits

* Improved accessibility
* Fewer support requests
* Better concession usage

---

## 6. Accessibility Recovery Suggestions

### Why it belongs here

Moderate impact because it affects users applying accessibility-related filters.

Medium effort because recommendation logic and alternative suggestions must be generated dynamically.

### Expected Benefits

* Reduced dead-end searches
* Better booking completion rates
* Improved accessibility experience

---

# Visual Matrix

```text
                HIGH IMPACT
                     ↑
                     │
                     │
                     │
     Quick Wins      │      Major Projects
                     │
 Persistent Filters  │  Tatkal Queue
 Auto Availability   │  Seat Lock System
                     │
─────────────────────┼────────────────────→
                     │
 Guided Concession   │
 Accessibility       │
 Recovery            │
                     │
       Fill-Ins      │      Time Sinks
                     │
                     ↓
                LOW IMPACT

                LOW EFFORT → HIGH EFFORT
```

---

# Recommended Roadmap

## Phase 1 (0–3 Months)

Implement:

1. Persistent Smart Filters
2. Auto Availability Loader
3. Guided Concession Assistant

Reason:

These provide immediate user value with minimal engineering effort.

---

## Phase 2 (3–6 Months)

Implement:

4. Accessibility Recovery Suggestions
5. Seat Preference Lock System

Reason:

Moderate engineering effort with significant usability improvements.

---

## Phase 3 (6–12 Months)

Implement:

6. Tatkal Virtual Queue System

Reason:

Largest engineering effort but highest long-term impact on platform stability and user trust.

---

# Final Recommendation

The recommended implementation order is:

1. Persistent Smart Filters
2. Auto Availability Loader
3. Guided Concession Assistant
4. Accessibility Recovery Suggestions
5. Seat Preference Lock System
6. Tatkal Virtual Queue System

This roadmap balances engineering effort with user impact and delivers meaningful improvements while preparing the platform for larger architectural upgrades.
