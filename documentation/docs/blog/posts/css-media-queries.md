---
drafts: false
tags: [css, html]
comments: true
date: 2024-05-02
authors:
  - bishow
---

# CSS Media Queries

CSS media queries are a powerful tool for creating responsive web designs. They allow you to apply different styles based on the characteristics of the device viewing the content, such as the `screen size`, `resolution`, `orientation`, and more. This way, you can ensure that your website looks good and functions well on a wide range of devices, from desktop monitors to smartphones.


<!-- more -->

## Media Queries

The ==@media== rule, introduced in `CSS2`, made it possible to define different style rules for different media types.

Media queries in `CSS3` extended the `CSS2` media types idea: Instead of looking for a type of device, they look at the capability of the device.

Media queries can be used to check many things, such as:

- width and height of the viewport
- orientation of the viewport (`landscape` or `portrait`)
- resolution

Using media queries are a popular technique for delivering a tailored style sheet to desktops, laptops, tablets, and mobile phones (such as iPhone and Android phones).


---


!!! success "Syntax"

    A media query consists of a ==media type== and can contain **one** or **more** media features, which resolve to either `true` or `false`.

    ```css title="CSS"
    @media not|only mediatype and (media feature) and (media feature) {
        ...
        /* CSS-Code; */
        ...
    }
    ```

    The mediatype is optional (if omitted, it will be set to all). However, if you use not or only, you must also specify a mediatype.


## Example

!!! abstract "Example"

    ```css
    /* On screens that are 992px or less, set the background color to blue */
    @media screen and (max-width: 992px) {
        body {
            background-color: blue;
        }
    }

    /* If screen size is more than 992px wide, set the font-size of <div> to 80px */
    @media screen and (min-width: 992px) {
        div.example {
            font-size: 80px;
        }
    }

    /* Orientation: Portrait / Landscape */
    @media only screen and (orientation: landscape) {
        body {
            background-color: lightblue;
        }
    }

    /* Min Width to Max Width:  */
    /* For example, when the browser's width is between 600 and 900px, change the appearance of a <div> element: */
    @media screen and (max-width: 900px) and (min-width: 600px) {
        div.example {
            font-size: 50px;
            padding: 50px;
            border: 8px solid black;
            background: yellow;
        }
    }


    /* When the width is between 600px and 900px or above 1100px - change the appearance of <div> */
    @media screen and (max-width: 900px) and (min-width: 600px), (min-width: 1100px) {
        div.example {
            font-size: 50px;
            padding: 50px;
            border: 8px solid black;
            background: yellow;
        }
    }
    ```


!!! note

    Meaning of the **not**, **only**, and **and** keywords:

    - `not`: This keyword inverts the meaning of an entire media query.
    - `only`: This keyword prevents older browsers that do not support media queries from applying the specified styles. It has no effect on modern browsers.
    - `and`: This keyword combines a media type and one or more media features.



You can also link to different stylesheets for different media and different widths of the browser window (viewport):


```html title="html"
<link rel="stylesheet" media="print" href="print.css">
<link rel="stylesheet" media="screen" href="screen.css">
<link rel="stylesheet" media="screen and (min-width: 480px)" href="example1.css">
<link rel="stylesheet" media="screen and (min-width: 701px) and (max-width: 900px)" href="example2.css">
```

## CSS Media Types

| Value       | Description                                           |
| ----------- | ----------------------------------------------------- |
| `all`       | Used for all media type devices                       |
| `print`     | Used for print preview mode                           |
| `screen`    | Used for computer screens, tablets, smart-phones etc. |


## CSS Common Media Features

Here are some commonly used media features:

| Value          | Description                                           |
| -------------- | ----------------------------------------------------- |
| `orientation`  | Orientation of the viewport. Landscape or portrait    |
| `max-height`   | Maximum height of the viewport                        |
| `min-height`   | Minimum height of the viewport                        |
| `height`       | Height of the viewport (including scrollbar)          |
| `max-width`    | Maximum width of the viewport                         |
| `min-width`    | Minimum width of the viewport                         |
| `width`        | Width of the viewport (including scrollbar)           |


---

## Reference

- [CSS Media Queries: w3schools](https://www.w3schools.com/css/css3_mediaqueries.asp)
- [Responsive Web Design - Media Queries: w3schools](https://www.w3schools.com/css/css_rwd_mediaqueries.asp)
- [Using media queries: developer.mozilla.org](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_media_queries/Using_media_queries)
- [CSS3 mediaqueries](https://www.w3schools.com/css/css3_mediaqueries_ex.asp)
- [CSS RWD Mediaqueries: w3schools](https://www.w3schools.com/css/css_rwd_mediaqueries.asp)


---
