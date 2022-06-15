# Customize the appearance of the Confirmed Booking ticket page

Confirmed Booking ticket page is the page that the user sees after booking an appointment.

![](/assets/draft-ticket.png ":size=400")

You can customize the appearance of this page by using CSS.

Enter your custom CSS into the `Add brand guidelines with CSS to your queue solution UI` input field inside the Settings of your Queue. 

Elements are targeted via data-theme attributes.

## Available attributes

List of available data-theme attributes and the corresponding elements. Look at examples to see how to use the properties inside css. Check the screenshots section for reference to each number.


| #   | data-theme attribute                  | description                          |
| --- |---------------------------------------|--------------------------------------|
| 1   | page__position                        | page background                      |
| 2   | queue-common__header                  | logo and title area                  |
| 3   | page-position__confirmation-messag    | booking confirmation message         |
| 4   | page-position__booking-info           | content area                         |
| 5   | page-position__booking-info__date     | booking date                         |
| 6   | page-position__booking-info__time     | booking time                         |
| 7   | page-position__booking-info__visitors | booking visitor                      |
| 8   | page-position__booking-info__location | booking location                     |
| 9   | page-position__booking-info__warning  | booking warning message              |
| 10  | page-position__position-actions       | buttons area                         |
| 11  | page-position__button-reschedule      | reschedule button                    |
| 12  | page-position__button-cancel          | cancel button                        |

## Reference Screenshots

On this screenshot every number refers to an attribute as specified in the table above.

![](/assets/draft-ticket-ref.png ":size=400")

## Examples

For using the `data-theme` attribute, take a look at the example below. This is how you format the attribute inside css.

```css
[data-theme="queue-common__header"] {
    background: lightblue;
}
```

This will change the header background color to lightblue.
