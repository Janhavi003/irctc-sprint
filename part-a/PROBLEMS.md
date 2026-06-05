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

# Problem 4: Availability Information Requires Manual Refresh [Self-Discovered]

## How I found it

While searching trains between Pune Junction and KSR Bengaluru, I attempted to compare seat availability across different classes.

## Screenshot / Description

Screenshot: `assets/screenshots/problem4-availability-refresh.png`

The train results page displayed "Refresh" buttons under each class (Sleeper, 3A, 2A, 1A) instead of immediately showing seat availability and waitlist information.

## What is broken

Train availability is not displayed automatically. Users must manually refresh every class individually before seeing availability information.

## Affected users

* Users comparing multiple classes
* First-time travelers
* Mobile users
* Time-sensitive passengers

Estimated impact: Most users performing train searches.

## Frequency

Occurs every time train-search results are displayed.

## Current flow — step by step

1. User enters source station, destination station, and travel date.
2. User clicks Search.
3. Train results load.
4. User wants to compare availability across classes.
5. Availability information is not displayed.
6. User sees separate Refresh buttons for each class.
7. User clicks Refresh for Sleeper.
8. Availability loads for Sleeper only.
9. User repeats the process for other classes.
10. User finally compares options.

## Where exactly it breaks

Step 5.

Critical booking information is hidden behind multiple manual refresh actions, increasing effort and slowing decision-making.

---

# Problem 5: Concession Options Lack Context and Guidance [Self-Discovered]

## How I found it

While exploring the train-search homepage and reviewing booking options available to passengers.

## Screenshot / Description

Screenshot: `assets/screenshots/problem5-concession-options.png`

The booking form displays options such as "Person With Disability Concession" and "Railway Pass Concession" without explaining eligibility requirements, benefits, documentation requirements, or usage instructions.

## What is broken

Important concession options are presented without sufficient context, forcing users to leave the booking flow and search elsewhere for information.

## Affected users

* Senior citizens
* Passengers with disabilities
* Railway pass holders
* First-time users

Estimated impact: Thousands of passengers seeking concession benefits every day.

## Frequency

Occurs whenever users attempt to understand concession eligibility during booking.

## Current flow — step by step

1. User opens the booking page.
2. User notices concession-related checkboxes.
3. User wants to know whether they qualify.
4. User looks for eligibility information.
5. No explanation is available on the booking screen.
6. User opens help pages or external websites.
7. User searches for documentation requirements.
8. User returns to the booking flow.
9. User remains uncertain about eligibility.
10. User either skips the concession or proceeds without confidence.

## Where exactly it breaks

Steps 4–6.

The booking flow provides options but not the information necessary to make informed decisions.

---

# Problem 6: Disability Concession Search Creates Dead-End Results [Self-Discovered]

## How I found it

While testing the "Person With Disability Concession" option and searching trains between Pune Junction and KSR Bengaluru.

## Screenshot / Description

Screenshot: `assets/screenshots/problem6-disability-concession-filter.png`

After selecting the disability concession option and choosing First Class, the results page displayed "0 Results" and the message "No trains are available for the filter(s) you have selected."

## What is broken

When accessibility-related filters produce no results, the system provides no explanation or recovery guidance.

## Affected users

* Passengers with disabilities
* Caregivers booking tickets on behalf of disabled passengers
* Users requiring concession-based travel

Estimated impact: All users attempting to book through disability-concession filters.

## Frequency

Occurs whenever selected concession and class combinations produce no matching trains.

## Current flow — step by step

1. User opens the booking page.
2. User selects "Person With Disability Concession."
3. User chooses a travel route.
4. User selects a class.
5. User clicks Search.
6. Search results return zero trains.
7. System displays "No trains are available for the filter(s) you have selected."
8. User receives no explanation.
9. User does not know which filter caused the problem.
10. User must manually experiment with different combinations.

## Where exactly it breaks

Steps 7–9.

The system identifies that no results exist but fails to explain why or suggest alternative options, creating a dead-end experience for users who depend on accessibility features.

---

## Conclusion

The three self-discovered problems reveal issues in information visibility, accessibility, and search usability:

1. Availability information requires unnecessary manual refresh actions.
2. Concession-related features lack contextual guidance.
3. Accessibility filters can lead users into dead-end search experiences without recovery options.

Together with the three given problems, these findings provide a comprehensive understanding of key pain points within the IRCTC booking experience and establish a strong foundation for Part B solution design.

## Conclusion

The three documented issues represent major reliability and usability challenges within the IRCTC booking experience:

1. Tatkal booking instability during peak demand.
2. Unreliable search and filtering behavior.
3. Loss of seat-selection preferences during booking.

These findings establish the foundation for further investigation and solution design in Part B of the IRCTC Design Engineering Sprint.
