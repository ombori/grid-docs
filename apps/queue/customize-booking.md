# Customize the appearance of the Booking page

You can customize the appearance of the booking page by using CSS. 

Enter your custom CSS into the `Add brand guidelines with CSS to your queue solution UI` input field inside the Settings of your Queue. 

Elements are targeted via data-theme attributes. 

## Available attributes
List of available data-theme attributes and the corresponding elements. Look at examples to see how to use the properties inside css. Check the screenshots section for reference to each number

| #   | data-theme attribute                              | description                          |
| --- | ------------------------------------------------- | ------------------------------------ |
| 1   | booking-page__wrapper                             | page background                      |
| 2   | queue-common__header                              | logo and title area                  |
| 3   | booking-page__subtitle                            | subtitle area                        |
| 4   | booking-page__card                                | the main content area                |
| 5   | booking-page__datepicker                          | datepicker header                    |
| 6   | booking-page__datepicker__choose-week             | header week area                     |
| 7   | booking-page__datepicker__weekdays                | header days listing                  |
| 8   | booking-page__datepicker__weekdays__day--selected | header active day selection          |
| 9   | booking-page__datepicker__weekdays__day           | header non-active day                |
| 10  | booking-page__list                                | available timeslots listing          |
| 11  | booking-page__timeslot                            | single timeslot                      |
| 12  | booking-page__timeslot__form__info                | info box on the active timeslot      |
| 13  | booking-page__timeslot__form                      | input fields on the active timeslot  |
| 14  | booking-page__timeslot_form__submit               | submit button on the active timeslot |

## Reference Screenshots
On these screenshots every number refers to an attribute as specified in the table above.

| ![](/assets/booking-customize-1.png ":size=400") | ![](/assets/booking-customize-2.png ":size=400") |
| ------------------------------------------------ | ------------------------------------------------ |
| ![](/assets/booking-customize-3.png ":size=400") | ![](/assets/booking-customize-4.png ":size=400") |


## Examples

For using the `data-theme` attribute, take a look at the example below. This is how you format the attribute inside css.

```css
[data-theme="booking-page__datepicker"] {
    background: lightblue;
}
```
This will change the datepicker header color to lightblue
![](/assets/booking-customize-datepicker-header.png ":size=400")

To edit the CSS of a particular element that doesn’t have an assigned data-theme attribute, you can target that element in reference to an element that does have an assigned attribute
```css
[data-theme="booking-page__timeslot"] > button span:nth-child(2) {
    background: lightblue;
}
```
![](/assets/booking-customize-datepicker-bookbutton.png ":size=400")
