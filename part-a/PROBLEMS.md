# IRCTC Problem Discovery — Part A

## Summary

* Total problems documented: 3 (Given Problems)
* Platform explored: irctc.co.in
* Devices used: Desktop Chrome
* Objective: Understand and document the most critical reliability and usability issues affecting IRCTC users.

---

# Problem 1: Tatkal Booking Crashes at 10:00 AM [Given]

## What is broken

The IRCTC platform becomes extremely slow or completely unresponsive when Tatkal booking opens at 10:00 AM. Users experience loading loops, session timeouts, CAPTCHA resets, OTP delays, and server errors. The system provides little or no information about what is happening during the failure.

## Affected users

* Tatkal travelers
* Emergency travelers
* Students
* Migrant workers
* Business travelers

Estimated impact: 20–40 lakh users attempting Tatkal booking during the opening window.

## Frequency

Occurs daily during Tatkal booking hours, especially between 9:58 AM and 10:05 AM.

## Current flow — step by step

1. User opens IRCTC around 9:50 AM.
2. User logs in and searches for the desired train.
3. User selects Tatkal quota.
4. User fills passenger details and reviews booking information.
5. User waits for Tatkal booking to open.
6. User clicks "Book Now" at approximately 10:00 AM.
7. Loading spinner appears and the page becomes unresponsive.
8. User receives a timeout, CAPTCHA reset, logout, or server error.
9. User refreshes the page and attempts to log in again.
10. Tatkal quota is already exhausted.

## Where exactly it breaks

Steps 6–8.

The booking request reaches the system during a massive traffic spike. Users receive no queue position, progress indicator, or meaningful explanation of the failure, causing confusion and repeated booking attempts.

---

# Problem 2: Search Filters Do Not Work Reliably [Given]

## What is broken

Train search filters such as class, quota, departure time, and availability do not always return accurate results. Filters may reset unexpectedly after navigation, forcing users to repeat their search process.

## Affected users

* First-time users
* Senior citizens
* Travelers comparing multiple train options
* Users booking on mobile devices

Estimated impact: Most users who perform train searches on the platform.

## Frequency

Intermittent, but more noticeable during periods of high traffic.

## Current flow — step by step

1. User enters source station, destination station, and travel date.
2. User clicks Search.
3. Search results appear.
4. User applies Sleeper Class filter.
5. User applies Available Seats filter.
6. Results refresh.
7. Some trains displayed do not match selected filters.
8. User opens a train to inspect details.
9. User navigates back to the results page.
10. Previously selected filters are lost or require reapplication.

## Where exactly it breaks

Steps 6–10.

Filter selections and refreshed train data are not consistently synchronized, resulting in inaccurate results and loss of user trust.

---

# Problem 3: Seat Selection Resets Randomly [Given]

## What is broken

Passengers who select a preferred berth sometimes lose their selection during the booking process. The system may replace the selected berth with automatic allocation or another seat.

## Affected users

* Families traveling together
* Senior citizens
* Passengers with disabilities
* Travelers requiring lower berths

Estimated impact: 30–40% of bookings where berth preference is important.

## Frequency

Occurs intermittently, with a higher occurrence reported on mobile devices.

## Current flow — step by step

1. User searches for a train.
2. User selects class and quota.
3. User opens the seat-selection screen.
4. User selects a preferred lower berth.
5. Selected berth is highlighted.
6. User clicks Proceed.
7. Passenger details page loads.
8. Preferred berth is replaced by Auto allocation or another berth.
9. User returns to the seat-selection page.
10. Previously selected berth may no longer be available.

## Where exactly it breaks

Between steps 5 and 8.

The seat-selection state is not consistently carried between booking screens, causing the user's preference to be lost before confirmation.

---

## Conclusion

The three documented issues represent major reliability and usability challenges within the IRCTC booking experience:

1. Tatkal booking instability during peak demand.
2. Unreliable search and filtering behavior.
3. Loss of seat-selection preferences during booking.

These findings establish the foundation for further investigation and solution design in Part B of the IRCTC Design Engineering Sprint.
