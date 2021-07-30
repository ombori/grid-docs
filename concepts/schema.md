# Settings Schema
Apps have a settings schema you can use to let people configure the apps they install. This is applicable for both IoT and Screen applications, but also applies to modules.


## Default Schema
Every app starts with a default `tsx` schema, which looks like this.

```javascript
export type Settings = {
  /**
   * @title A test setting
   * @default "Default value"
   */
  testSetting: string;
}

```

## Schema Structure
There are 3 relevant lines in the schema, let's explain them all.

**Title**

This is the title that will be visible in the console once you have the app installed.
```javascript
   * @title A test setting
```

**Default**

Default is the value that will be prefilled in the input field, keep in mind it has to be put in quotes like shown below. 
```javascript
   * @default "Default value"
```

**Variable Definition**

The last important line is the variable definition
```javascript
  testSetting: string;
```

`testSetting` is the variable you will receive in your module, and `string` is the type of the variable.

Supported variable types are

- string
- number
- boolean - *will render as a checkbox*
- array - *an array of defineable objects*

## Array definition
To define an array, you can't simply put in `array` as type, but you need to specify your definition. For example, if you want an array with object with string input, then you need to define this as an input field like this.

```javascript
type MyCustomObject = {
  /**
   * @title Array String Item
   * @default "Default value"
   */
    name: string;
}
```

Then you can set this for the array definition below the original definition already in place.

```javascript
export type Schema = {
  /**
   * @title Multiple Inputs
   */
  items: MyCustomObject[];
}
```

## Optional Settings
By default all fields you've defined in the settings are mandatory, if you want to make them optional you need to add a `?` to the variable definition.

```javascript
  testSetting?: string;
```