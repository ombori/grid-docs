# Queue Manager Release notes
The Queue Manager receives continuous updates. All the recent release notes can be found below in order of release. 

## 2021-11-22
#### Changes
- New waiting time mechanism: now we will use more accurate mechanism for time prediction. 
If serving mode and email login flow are enabled we will take average serving time, divide by amount of active counters / sales persons (active users in Queue manager) and multiply by ticket number in the queue.
If it's not serving or it's pin login flow, for idea above instead of exact serving time we will consider time difference between two tickets called into location. Amount of active counters / sales persons will be always 1.
- Staff notifications: system won't send notifications about waiting time if there are no people in queue 

### Features
- Auto checkout: now you can specify time after which tickets from "Serving" column are checked out automatically

#### Bugfixes
- Fixed information about Active Directory users for servedBy property
- Fixed enabling iOS notifications when SMS and emails and collecting customer information are disabled 
- Fixed ability to create two booking for the same slot if timezone for queue and customer is different (only when there special hours which are the same by day of week and time)

## 2021-11-17
#### Features
- Order pickup: Customers will be able to Cancel order pickup
- Order pickup: Customers will be able to send feedback about the order pickup experience

#### Bugfixes
- Fixed duration label for bookings
- Fixed notifications for disabled both SMS and email notifications 

## 2021-11-11
#### Changes
- Added verification by email if the booking is using emails only.
- Now on the booking page, the customer will see timeslot durations instead of time range.
- New logic for Special bookings hours: Values only from this section will be applied for the specified date. Settings from regular hours or Separate bookings hours will be overwritten.
- In the queue manager UI, serving person initials will be created from the person's display name if possible. Otherwise, the email address will be used.

#### Features
- Order pickup: now in Order manager UI you will be able to find all links for issued orders which weren't booked by customers yet

#### Breaking change

!> New logic for Special bookings hours: Values from this section will only be applied for the specified date. Settings from regular hours or from Separate bookings hours won't be used at all.

## 2021-10-12
#### Changes
- Added registration information to the booking calendar. Now, staff can get booking information directly from the calendar.
- Updated integration method for bambuser. Instead of configuration on Tenant level, it is now configured on Queue level.
- Added order number on the order pickup ticket page
- Added customizations for SMS messages: 
    - Ticket rejected from the Queue Manager
    - Booking canceled by Queue Manager in the calendar
    - Order pickup confirmation
    - Order pickup link generated message.

## 2021-10-01
#### Changes
- Updated email templates
- Added time range for booking confirmation

#### Bugfixes
- Bambuser: Improved digital call calling logic for sounds (will stop the sound when it's picked up by another staff member)

## 2021-09-27
#### Changes
- Updated description for default email template
- Queueing time calculation for analytics is now based on time between ticket creation and calling forward, previously it was until the ticket was checked-in instead.

#### Bugfixes
- Fixed a bug that webhooks are not preserved after the queue has been updated and saved
- Fixed a bug with connecting to Digital call

## 2021-09-20
#### Bugfixes
- Fixed a bug that iOS notifications were not working after configuring them.

## 2021-09-09
#### Changes
- Categories: You can now set up custom labels for different categories in the Console. This will reflect in the customer registration flow (customer will have to specify category) and it will be shown in queue manager UI.

**How do you use it?** First, specify the categories, then add the type *Categories* in the registration flow section. You can see how it looks in the screenshots below.

|                                                                                      |                                                                                                    |                                                                                 |
| ------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------- |
| ![](/assets/specify-custom-categories-console-septebmer-2-week-2021.png ":size=400") | ![](/assets/specify-custom-categories-console-registrattion-septebmer-2-week-2021.png ":size=400") | ![](/assets/specify-custom-categories-QM-septebmer-2-week-2021.png ":size=400") |

- Added `queueId` property as a piece of extra information in *Bambuser* call link
- Improved the update-mechanism for recalculation of position in the queue and waiting time. Now for smaller queues update is almost instant.
- Added support for 12-hours and 24-hours clocks in SMS for curbside and bookings

#### Bugfixes

- Fixed initials in Queue manager view. This should now be consistent after booking is assigned and serving has started.

## 2021-08-31
#### Changes
- Staff notifications - now we can send emails to staff when the email feature is enabled if conditions are met. For example when the waiting time is too long. 

![](/assets/staff-notifications-31-aug-2021.png ":size=400")

#### Bugfixes
- Fixed translation messages for order pickup and walk-in tickets
- If no Occupancy feature is active, you won’t see Occupancy related fields in Queue Manager UI
- Fixed a bug with incorrect notification type when only email notification type is specified
- Fixed a bug with incorrect labeling when an order pickup ticket has the same order id within two queues for the same organization.

## 2021-08-24
On August 28th 2021 we released a new minor version of the Queue Manager, this is visible in the settings screen.

#### Changes
No new features have been added to this release.

#### Bugfixes
- Fixed curbside pickup minor bugs, for example, the logic for sending the first reminder.
- Reduced amount of requests to the database for optimization.
- Internal stabilization.

## 2021-08-04
#### Changes
Added a "blocked days" feature for booking, this allows you to prevent booking within `#` amount of days. 

![](/assets/20210804-blocked-days.png ":size=400")

The "Blocked days" feature allows you to specify the minimum amount of days you want bookings to be booked in advance. Setting this to 7 means the first possible date bookings can be scheduled for is a week from now, and 1 allows it starting from tomorrow.

#### Bugfixes
This version had a minor bugfix that caused an issue with booking in a very specific situation