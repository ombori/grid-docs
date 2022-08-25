# Customize the appearance of the Walk-in ticket page

Walk-in ticket page is the page that the user sees after creating a walk in (by scanning QR code) ticket.

![](/assets/walk-in-ticket.png ":size=400")

You can customize the appearance of this page by using CSS.

Enter your custom CSS into the `Add brand guidelines with CSS to your queue solution UI` input field inside the Settings of your Queue. 

Elements are targeted via data-theme attributes.

## Available attributes

List of available data-theme attributes and the corresponding elements. Look at examples to see how to use the properties inside css. Check the screenshots section for reference to each number.


| #   | data-theme attribute                               | description                                                                            |
| --- |----------------------------------------------------|----------------------------------------------------------------------------------------|
| 1   | page__position                                     | page background                                                                        |
| 2   | queue-common__header                               | logo and title area                                                                    |
| 3   | queue-common__position-ticket                      | ticket info area                                                                       |
| 4   | queue-common__position-ticket__number              | ticket number                                                                          |
| 5   | queue-common__position-ticket__people-ahead        | people ahead                                                                           |
| 6   | queue-common__position-ticket__visitors-amount     | amount of visitor (only visible if amount of visitors is not editable)                 |
| 7   | queue-common__position-ticket__people-number       | amount of visitors that user can edit (only visible if amount of visitors is editable) |
| 8   | queue-common__position-ticket__notification-button | notification button                                                                    |
| 9   | queue-common__info-message                         | safe distance warning message                                                          |
| 10  | page-position__position-actions                    | buttons area                                                                           |
| 11  | page-position__button-reschedule                   | reschedule button                                                                      |
| 12  | page-position__button-cancel                       | cancel button                                                                          |

## Reference Screenshots

On this screenshot every number refers to an attribute as specified in the table above.

![](/assets/walk-in-ticket-ref.png ":size=400")

## Examples

For using the `data-theme` attribute, take a look at the example below. This is how you format the attribute inside css.

```css
[data-theme="queue-common__header"] {
    background: lightblue;
}
```

This will change the header background color to lightblue.
