# Queue Manager Release notes
The Queue Manager receives continuous updates. All the recent release notes can be found below in order of release. 

## 2021-08-31
On August 31th 2021 we released a new minor version of the Queue Manager, this is visible in the settings screen.

### Changes
- Staff notifications - now we can send emails to staff when the email feature is enabled if conditions are met. For example when the waiting time is too long. 

![](/assets/staff-notifications-31-aug-2021.png ":size=400")

### Bugfixes
- Fixed translation messages for order pickup and walk-in tickets
- If no Occupancy feature is active, you won’t see Occupancy related fields in Queue Manager UI
- Fixed a bug with incorrect notification type when only email notification type is specified
- Fixed a bug with incorrect labeling when an order pickup ticket has the same order id within two queues for the same organization.

## 2021-08-24
On August 28th 2021 we released a new minor version of the Queue Manager, this is visible in the settings screen.

### Changes
No new features have been added to this release.

### Bugfixes
- Fixed curbside pickup minor bugs, for example, the logic for sending the first reminder.
- Reduced amount of requests to the database for optimization.
- Internal stabilization.

## 2021-08-04
On August 4th 2021 we released a new minor version of the Queue Manager, this is visible in the settings screen.

### Changes
Added a "blocked days" feature for booking, this allows you to prevent booking within `#` amount of days. 

![](/assets/20210804-blocked-days.png ":size=400")

The "Blocked days" feature allows you to specify the minimum amount of days you want bookings to be booked in advance. Setting this to 7 means the first possible date bookings can be scheduled for is a week from now, and 1 allows it starting from tomorrow.

### Bugfixes
This version had a minor bugfix that caused an issue with booking in a very specific situation