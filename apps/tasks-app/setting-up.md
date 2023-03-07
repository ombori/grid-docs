# Setting up Tasks App

## Installation
1. Find the "Tasks" app in the Marketplace > Apps and click Install.
2. Provide the installation name and the installation group where you want to create the installation
3. Press OK and installation will be created

## Configuration
Indicated numbered items below are the important settings required to setup a running tasks app.
Other items not explained can be skipped.

![](/assets/header-tabs.png ":size=800")

1. **Installation Name**
2. **Settings Tab**
    - Shows the tasks app settings content
3. **Queue Status** 
    - Indicates whether the queue is open or closed
    - Status should be "open" in order for solutions integration to work

---
### General Settings
![](/assets/general-settings.png ":size=700")

4. **Timezone**
    - Indicates the timezone the app will be running
5. **Title** 
    - Title to be displayed on the Tasks Manager
6. **Show Serving Tab**
    - Check this option to show 3rd column (for delivered items) of the Tasks Manager
7. **Tasks manager link**
    - Quick access link to the Tasks App manager
8. **Save changes**
    - Button to save and apply changes to the installation

---
### Select Login Method
![](/assets/login-method.png ":size=500")

9. **Login method**
    - Indicates which login method to use in Tasks App manager
        - Pin code -> Login using specified pin code only
        - Email -> Login using specified and valid Grid Console user emails
10. **Pin code**
11. **Emails**

---

### Configure Required Settings
![](/assets/custom-settings-checkbox.png ":size=500")

12. Next, you'll need to check `Collect customer's information` checkbox
---
![](/assets/custom-settings-add-input.png ":size=500")

13. Add new fields by selecting "Input" and pressing "+" button
- Set of fields are indicated in numbers 14-17
---
![](/assets/custom-settings-gridSignals.png ":size=500")

14. Add a new input and set the following details:
- **Name**: gridSignals
- **Value**: 
```
{"tenantId": <Tenant's ID>, "spaceId": <Location's ID>, "dataResidency": <Tenant's Data Residency>, "country": <Tenant's Country code>, "appId": <Installation's ID>, "installationId": <Installation's ID>}
```

Where to get the values of each item in "Value" field?
- Tenant's ID - taken on the console URL after `organisations/`
![](/assets/url-tenantId.png ":size=700")
- Location's ID - taken on the specific location's URL in console after `spaces/`
![](/assets/url-locationId.png ":size=700")
- Data Residency - either `EU`, `US`, `IN`, `UAE`, `AU`
- Country - country codes
- Installation's ID - taken on Tasks App installation URL in console after `apps/`
![](/assets/url-installationId.png ":size=700")

---

![](/assets/custom-settings-order.png ":size=500")

15. Add a new input and set the following details:
- **Name**: orderCategories
- **Value**: `[{"smart-fitting-room": "Smart Fitting Room"}, {"endless-aisle": "Endless Aisle"}]`
---
![](/assets/custom-settings-deviceId.png ":size=500")

16. (OPTIONAL) If deviceId checking is required (Example is external inventory check by device ID), add a new input and set the following details:
- **Name**: deviceId
- **Value**: `<Device ID value>`
---
![](/assets/custom-settings-enableFetchInventory.png ":size=500")

17. (OPTIONAL) If external inventory checks is required (Example is external inventory check for FOH/BOH availability), add a new input and set the following details:
- **Name**: enableFetchInventory
- **Value**: `true`


## Tasks Manager
![](/assets/tasks-login.png ":size=700")

Next step would be to open the Tasks Manager link and login

![](/assets/tasks-header-setting.png ":size=700")

Click on the "Settings" icon in the upper right corner

![](/assets/tasks-settings.png ":size=700")

Toggle in Queue settings to "Open" the queue

**Important Note**: The Queue should be Open before integrating the Tasks App to other solutions like Endless Aisle and Smart Fitting Room

### For Preparation
![](/assets/tasks-for-preparation.png ":size=700")

The 1st column represents the tasks added to the queue that are yet to be prepared
1. **Ticket Number**
2. **Device Name where task was requested**
3. **Time when the ticket was created**
4. **Tags**
5. **Product details**
6. **Prepare Button** - this moves the ticket to "Preparing" column when pressed

### Preparing
![](/assets/tasks-preparing.png ":size=700")

The 2nd column represents the tasks that are currently being processed/prepared
1. **Remove** - removes the tasks from the queue
2. **Try later** - returns the task to the "For preparation" column
3. **Scan** - opens the scanner to scan barcode for inventory check
4. **Deliver** - marks the task as delivered and moves the ticket to the 3rd column

### For Payment / Completion
![](/assets/tasks-complete.png ":size=700")

The 3rd column represents the tasks that are already delivered and for completion
1. **Complete** - marks the task as completed and removes the ticket from the list