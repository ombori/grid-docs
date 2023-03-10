# Scheduled Maintenance - OmboriGrid Queue System

In relation to OmboriGrid’s initiative for ISO27001 certification, OmboriGrid will perform maintenance on Queue System infrastructure. This notice is intended for clients with existing OmboriGrid Queue System Solutions. There will be no new features that will be added, and no existing features that will be removed. All impacted solutions are expected to work normally before and after the scheduled maintenance.

## Schedule
| Region  | From                               | To                                 | Expected Unavailability Duration |
| ------- | ---------------------------------- | ---------------------------------- | -------------------------------- |
| EU      | March 15, 2023<br /> (20:00 UTC+0) | March 15, 2023<br /> (21:00 UTC+0) | 1 hour                           |                
| IN      | March 14, 2023<br /> (19:00 UTC+0) | March 14, 2023<br /> (20:00 UTC+0) | 1 hour                           |
| UAE     | March 14, 2023<br /> (20:00 UTC+0) | March 14, 2023<br /> (21:00 UTC+0) | 1 hour                           |
| US      | March 14, 2023<br /> (08:00 UTC+0) | March 14, 2023<br /> (09:00 UTC+0) | 1 hour                           |

## Impacted Applications
- Queue Management Solution
  - Queue Manager
  - Queue Ticket
  - All Queue Kiosk variants
  - All Queue Ticket Signage variants
- Occupancy Control Solution
- People Counter Solution
- Queue with Bambuser Solution
- Omni-visit Solution
- Appointment Booking Solution
- Order Pickup Solution
- Grid Mobile - with Tasks App

## Required Actions for Customers
- Avoid using the specified applications on the specified maintenance schedule. You might encounter some issues during the maintenance
- Verify and update your network whitelist (For customers using any Queue System Solutions behind a firewall)

  Below domains need to be included in your firewall whitelist, if not yet added.
  - api.omborigrid.com
  - `realtime-<region>.omborigrid.com`

    Pick the correct domain based on your region:
    - AU: realtime-au.omborigrid.com
    - EU: realtime-eu.omborigrid.com
    - IN: realtime-in.omborigrid.com
    - UAE: realtime-uae.omborigrid.com
    - US: realtime-us.omborigrid.com

  - `queue-<region>.omborigrid.com`
    Pick the correct domain based on your region:
    - AU: queue-au.omborigrid.com
    - EU: queue-eu.omborigrid.com
    - IN: queue-in.omborigrid.com
    - UAE: queue-uae.omborigrid.com
    - US: queue-us.omborigrid.com

  - `tasks-<region>.omborigrid.com`
    Pick the correct domain based on your region:
    - AU: tasks-au.omborigrid.com
    - EU: tasks-eu.omborigrid.com
    - IN: tasks-in.omborigrid.com
    - UAE: tasks-uae.omborigrid.com
    - US: tasks-us.omborigrid.com

## Questions and Concerns
Please contact OmboriGrid through your designated Customer Success Manager, or through our support email, support@ombori.com.