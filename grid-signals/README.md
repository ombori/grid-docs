# Grid Signals

!> Grid Signals is currently in pre-release. Breaking changes are not likely but can still occur before production release

Grid Signals is a library to manage sessions, identify users, and tie different sessions of the same user together. Furthermore, you can use it to manage spaces. A space within Grid Signals is a group of physical devices and virtual entities that share the same state in a physical location.

You could, for example, group all devices within a single store together as a space, and then track the activities of all users within that space. This is incredibly useful to understand what is happening within a space.

With Grid Signals, you can also track the activities of a single user across multiple devices. This is useful to understand what is happening within a single user's context. This can be useful when you hand over the session from a screen to the mobile device of the user. You can then easily transfer session information, like cart contents, or the current page, to the user without issues.

## Getting started
To get started with Grid Signals, it is recommended to go to the [Getting Started](/grid-signals/getting-started) page.

### Further Reading
Then there are several other pages that you can read about Grid Signals.

- [React App Integration](/grid-signals/react-app-integration)
- [NodeJS App Integration](/grid-signals/node-js-integration)
- [Event Tracking](/grid-signals/tracking-events)
- [States and Events](/grid-signals/states-and-events)

## Transparency and GDPR
To comply with GDPR we recommend informing your users about any information that can be tracked as a common practice. We do our best to protect your users' privacy, and for this, we have the Contacts API. Any personable information that is sent to Grid Signals using CONTACT_IDENTIFY or CONTACT_METADATA is stored separately from the session information, and only the session-id is used in tracking further events. However, when you send personable information through custom events there is no way for the API to know this is personal information that should be separated from generic data payloads.
