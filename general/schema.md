# Settings Schema
Apps have a settings schema you can use to let people configure the apps they install. This is applicable for both IoT and Screen applications but also applies to modules.


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
There are 3 relevant lines in the schema Let's explain them all.

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
To define an array, you can't simply put in `array` as type, but you need to specify your definition. For example, if you want an array with an object with string input, then you need to define this as an input field like this.

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

## Media Picker

```javascript
type Media = {
  ref: 'media';
  type: string;
  id: string;
  url: string;
};

export type Schema = {
  /**
   * @title Media
   * @ui mediaPicker
   */
   media: Media;
}
```

## Queue Picker

```javascript
type Queue = {
  /**
   * @title Queue ID
   */
  queueId: string;

  /**
   * @title Organisation name
   */
  organization: string;

  /**
   * @title Queue endpoint
   */
  queueEndpoint: string;
};

export type Schema = {
  /**
   * @title Queue
   * @ui queuePicker
   */
  queue: Queue;
}
```

## CSS field

```javascript
  /**
   * @title Css
   * @widget css
   */
  css: string;
```

## Mobile Endpoint picker

```javascript
  /**
   * @title Mobile endpoint picker
   * @ui mobileEndpointPicker
   */
  mobileEndpoint: any; // to add proper types
```

## Color picker

```javascript
  /**
   * @title Color Picker
   * @widget color
   */
  color: string;
```

## Textarea

```javascript
  /**
   * @title Text Area
   * @widget textarea
   */
  textarea: string;
```

## Javascript field

```javascript
  /**
   * @title Javascript
   * @widget javascript
   */
  js: string;
```

## Boolean

```javascript
  /**
   * @title Is gate open by default?
   * @default true
   */
  isOpenByDefault: boolean;
```



## Optional Settings
By default, all fields you've defined in the settings are mandatory If you want to make them optional, you need to add a `?` to the variable definition.

```javascript
  testSetting?: string;
```

## Roles
Apply a user-role level field visibility. You can use the default roles "admin" | "editor" | "viewer" or the ID of the custom role.

```javascript
  /**
   * @title Product price
   * @default "99 USD"
   * @roles ["admin", "editor"]
   */
  productPrice: string;
```
## Settings Overriding context visiblity
Apply a settings overriding context level field visibility. The options are "global" | "space" | "device". If not defined, it will be visible to all contexts.

```javascript
  /**
   * @title Product name
   * @default "My Example Product"
   * @settingsOverridingRule ["global", "space", "device"]
   */
  productName: string;
  productPrice: string;
```

## Space Picker
Pick a space and ability to

Available uiOptions:
- filterTypes: string
  - options: "location" | "sections" | "floor" | "custom"
- showOnlyWithExternalId: boolean

Example:

```javascript
  /**
   * @title Space
   * @ui spacePicker
   * @uiOptions { filterTypes: "location,sections", showOnlyWithExternalId: true }
   */
  space: { id: string; externalId: string };
```