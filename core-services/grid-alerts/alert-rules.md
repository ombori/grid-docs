# Grid Alerts - Alert Rules

An alert rule is a set of conditions based on device's health and device's associated analytics data. It also defines the actions to take, the Notification Group, when at least one of the conditions is met.

  ![](/assets/alert-rules-list.png ":size=512 :no-zoom")

## Creating or updating an Alert Rule

  ![](/assets/alert-rule-form.png ":size=512 :no-zoom")

### Name
The name of the Alert Rule

### Description
The description of the Alert Rule

### Is enabled
An option to enable or disable an alert rule. When disabled, the rule will be skipped in monitoring logic. When enabled, the rule will be considered when motoring the devices in real-time.

### Severity
The severity of the rule.

Available options:
  - Critical
  - Error
  - Warning
  - Information

### Scope
The scope of the devices to monitor.

#### Available scopes
  - Global - all devices in the tenant
  - All Spaces - all devices in all spaces
  - Specific space - devices under the specific space
  - All installations - all devices in all installations
  - Specific installation - devices under the specific installation
  - Combination of specific space and specific installation - devices under the specific space AND under the specific installation

### Conditions
The conditions that are checked during real-time device monitoring.

#### Available Conditions:
  - Device Status - when a device status changes after a specific period of time. When it changes to online from offline and failing, the condition is automatically met.
  - Device daily analytics session count - when a device has met the analytics session count based on the defined standard threshold or count operator.

#### Available Operators:
  - Greater than
  - Greater than or equal to
  - Less than
  - Less than or equal to

### Actions
A list of actions to take when at least one of the conditions is met. The options are from the list of the Notification Groups.
