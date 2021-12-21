# Grid Signals

Grid Signals is there for you to manage sessions, identify users, and tie different sessions of the same user together. Furthermore, you can use it to manage spaces. A space within Grid Signals is a group of physical devices and virtual entities that share the same state in a physical location.

You could, for example, group all devices within a single store together as a space, and then track the activities of all users within that space. This is incredibly useful to understand what is happening within a space.

With Grid Signals, you can also track the activities of a single user across multiple devices. This is useful to understand what is happening within a single user's context. This can be useful when you hand over the session from a screen to the mobile device of the user. You can then easily transfer session information, like cart contents, or the current page, to the user without issues.

## Getting started
To get started with Grid Signals, it is recommended to go to the [Getting Started](/grid-signals/getting-started) page.

### Further Reading
Then there are several other pages that you can read about Grid Signals.

- [Main Functions](/grid-signals/main-functions)
- [Standard Session Events](/grid-signals/standard-session-events)
- [Session API](/grid-signals/session-api)
- [States](/grid-signals/states)

## Transparency and GDPR
To comply with GDPR we recommend informing your users about any information that can be tracked as a common practice. We do our best to protect your users' privacy, and for this, we have the Contacts API. Any personable information that is sent to Grid Signals is stored separately from the session information, and only the session-id is used in tracking further events. However, when you sent personable information through custom events there is no way for us to know this is personal and should be split up.