# Order Pickup

Curbside pickup is a solution that allows your customers to book a slot. You will need to send your customers a unique link to book the slot, which you can read about in our [Vender Integration Documentation](https://ombori.atlassian.net/wiki/spaces/OAKB/pages/536346625/Curbside+pickup+Vendor+integration).

To install "Curbside Pickup", visit the Ombori Grid Marketplace in the console and find the "Order Pickup" Application.

## How to use order-pickup.
We've documented the administrator and customer user journeys to our documentation. Read more about how to use it there.

- [Administrator Journey](https://ombori.atlassian.net/wiki/spaces/OAKB/pages/214794413/Access+the+Curbside+Pickup+administrator)
- [User Journey](https://ombori.atlassian.net/wiki/spaces/OAKB/pages/214794491/Book+a+pickup+time+slot)

> Check the sidebar after clicking the links above for more journeys.

## Configuring opening times and capacity
Opening times are fundamental in configuring your pickup correctly. Opening time consists of a few configurations that are relevant to capacity and times.

First, there is "general settings". In this section, you can configure from when to when you are open. Multiple slots of time can be added per day, and days can be enabled/disabled separately. This section is the general store opening hours.

![](/assets/opening-hours.png ":size=400")

Next, there is a way to manage the capacity and the length of timeslots. This section is called "Curbside Pickup" in the settings overview.

![](/assets/curbside-timeslots.png ":size=300")

#### Timeslot duration
This is the duration of the timeslot that will be displayed to the customer. For example, if you configure 30 minutes, then the customer can pick options like 10:00, 10:30, 11:00, etc. If you configure 5 minutes then the options will be 10:00, 10:05, 10:10, etc.

#### Timeslot capacity
This setting is for how many bookings you can allow per timeslot. If you configure `1`, then only a pickup can be booked for that timeslot, this means if the next person tries to book a slot that option won't be visible.

#### Separate curbside pickup hours
This allows you to configure opening hours and capacity separately from the opening hours of your store. 

![](/assets/curbside-hours.png ":size=400")

As you can see in the image above we've configured to enable it on Monday only, and then also a custom capacity. This separate capacity field overrides the `Timeslot capacity` for the timeframe only.

## Log-in Method
To get into the admin panel you can configure how to access it. By default PIN-based login is enabled, and a random pin was generated when Order Pickup was installed. 

However, you can also opt-in to use email-based login, this is based on the available users added in your console. This way authentication is already handled.

![](/assets/login-method.png ":size=400")


## Notification Settings
![](/assets/notification-settings.png ":size=400")

You can customize notification settings.

| Field                       | Description                                                                |
| --------------------------- | -------------------------------------------------------------------------- |
| Enable push notifications   | Not Applicable for Order Pickup                                            |
| Enable Apple Wallet         | Not Applicable for Order Pickup                                            |
| Enable SMS                  | Send SMS messages to your users, you can customize the messages separately |
| Enable E-mail notifications | Not Applicable for Order Pickup                                            |

#### SMS customization
When you've enabled `Enable SMS` you will get additional fields you need to enter.

| Field                          | Description                                                                                                                                |
| ------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------ |
| Phone Number                   | Mandatory field. Phone number of the SMS gateway. Ask us for integration                                                                   |
| Code                           | Not applicable for Order Pickup                                                                                                            |
| Default Country                | Set the default phone number country, this will make entering phone numbers easier, but users are still able to select a different country |
| Allowed phone number countries | Enter phone number countries you want to support, if empty all countries are present                                                       |



## Text Customization
There are a lot of messages in the UI you can customize. You can find out about what each field means in our [documentation](https://ombori.atlassian.net/wiki/spaces/OAKB/pages/214761693/Curbside+Text+Communication+Customization).

### Microsoft Teams Integration
Microsoft Teams Integrations allows your employees to receive notifications of users arriving. This setup requires our integration as a bot user needs to be configured as well. Contact us if you're interested.

![](/assets/teams-integration.png ":size=500 :no-zoom")

## Customizing the design
To customize the design of the screens involved in the order pickup, you can make a few changes.

#### Add a logo
At the `General Settings` you can configure the URL of the logo you want to display on the booking page. You can upload your image to the Media Library. Open the media item using the `edit` button and you can copy the URL from there.

#### Customizing CSS
You can provide custom CSS in the CSS field. For more information on how to customize this, contact us on [Slack](https://join.slack.com/t/slack-pgo5586/shared_invite/zt-s1ajca83-k8i1f2mqgCMD0vDfpCk4Bg).

