# Cascading Style Sheet Notes
It is a language used to describe the `style` of document.

## Basic Syntax
```
h1 {
    color: red;
}
```
* `Selector` The selected elements like `h1` in above example.
* `Property` The property that is to be changed like `color` which will change text color.
* `Value` Setting the `value` of the property.

## Including Style
* Inline
```
<h1 style="color:red">Text</h1>
```
* Style Tag
```
<style>
    h1 {
        color:red;
    }
</style>
```
* External Stylesheet
```
<link ref="stylesheet" href="style.css" />
```

## Style Priority
* Inline style have highest priority.
* In stylesheet page the priority increases from top to bottom.

## Color Property
Used to set color of foreground (text, button text, link text).
```
color: red
```

## Background Color Property
Used to set color of Background.

## Color Systems
* RGBA (red (0-255), green (0-255), blue (0-255), alpha/opacity (0-1))
```
color: rgb(255, 0, 0, 1);
```
* Hexadecimal (numbers based on 16 digits (0-9 and a,b,c,d,e,f) just like our counting which have 10 digits 0-9 and called decimal numbers and binary numbers based on 2 digits 0 and 1). Instead of 0-255 value of RGB we use hexadecimal value 0-ff.
```
color: #00ff00
```

## Selectors
* Universal `* {}` select all elements of the document.
* Element `h1 {}` select html element using tag name.
* ID select `#givenID {}` select html element using id.
* Class `.myClass {}` select html elements using class.

## Text Properties
* `text-align: left/right/center` Used to align text in an element.
* `text-decoration: blue dotted underline/overline/line-through` Used to underline or have similiar formatting for text.
* `font-weight: normal/bold` Set text to light or dark text.
* `font-family: ariel` Set font type.
* `font-size: 2px` Set font size.
* `line-height: 20px` Set line height.
* `text-transform: uppercase/lowercase/capitalize` Transform text to different styles.

## Units in CSS
* Absolute (`1 inch = 96px = 2.54 cm = 25.4 mm`)
    * centimeter `cm`
    * inch `in`
    * milimeter `mm`
    * pixel `px`
* Relative
    * `%` Percent relative to parent div size
    * `em` Used for fonts related styles. 2em = 2 times font size of the parent.
    * `rem` Root em. Time multiple of root font size element.
    * `vh` Relative to 1% of viewport height
    * `vw` Relative to 1% of viewport width

## Box Model
* `height`
* `width`
* `padding` clockwise values `: top right bottom left`
* `margin` clockwise values `: top right bottom left`
* `border`, `border-radius`
```
          |-------Width-------|
   _ _     ___________________                ___________
    |     |    ___________    |              |           |
    |     |   |           |   |              |           |
  Height  |   |  Content  |   | <--Margin--> |           |
    |     |   |___________|   |              |           |
   _|_    |         |         |              |___________|
          |------Padding------|
          |_________|_________|
                  Border
```

## Create Circle from `div`
Create a `div` having `width` same as `height` and then set `border-radius` to `50%`.

## Display Property
* `inline` Takes only space required by the element. No margin/padding/width/height.
* `block` Taken full space available in width.
* `inline-block` Same as inline but we can set margin/padding/width/height.
* `none` Remove element from document UI like it don't exist.

## Visibility
`visibility: hidden` Removes the element from document UI but keeps its space reserved.

## Position Property
How element is positioned in document.
```
position: static/relative/absolute/fixed;
```
* `static` default position. The `top`, `right`, `bottom`, `left` and `z-index` properties have no effect.
* `relative` element is relative to itself. The `top`, `right`, `bottom`, `left` and `z-index` properties will work.
* `absolute` position relative to its closest parent non static element. Removed from document flow.
* `fixed` position relative to browser. Removed from document flow.
* `sticky` position depending on user' scroll

## z-index Property
By defualt element priority is increased from top to bottom. But we can set `z-index` to set priority to handle overlapping div.

## Background Image Property
* `background-image: url("cat.jpg");`
* `background-size`
    * `cover` Fill completely
    * `contain` Image will repeat
    * `auto` default value full size of the image.

## Flexbox
We have 2 axis main and cross axis. Main axis is the axis of direction of flexbox.
* `display: flex;`
* `flex-direction: row;` Direction of flexbox can be set to `row` (defaul), `row-reverse`, `column` and `column-reverse`
* `flex-wrap` Specifies whether the flex items should wrap or not. Values can be `nowrap`, `wrap`, or `wrap-reverse`.
* `justify-content: flex-start` Alignment along the main axis. Values can be `flex-end`, `center`, `space-around` and `space-evenly`.
* `align-items` Aligns the flex items when they do not use all available space on the cross-axis.
* `align-content` Aligns the flex lines when there is extra space in the cross axis and flex items wrap.
* `align-self` Align a single flex item.
* `flex-gorw` Grow flex item.
* `flex-shrink` Shrink flex item.

## Media Queries
Helps create websites responsive.
```
@media (min-width: 600px) and (max-width: 800px) {
    div {
        color: red;
    }
}
```

## Pseudo Class
A CSS pseudo-class is a keyword that can be added to a selector, to define a style for a special state of an element.
```
selector:pseudo-class-name {
  CSS properties
}
```

## Transitions
Change the transition properties of elements. `duration`, `timing-function` and `delay`.
```
transition: property duration timing-function delay;
```

## Transform
Used to apply 2D or 3D transformations to an element.
* `rotate` Rotate element.
* `scale` Change size of element.
* `translate` Move the element from current position.
* `skew` Strech element.
```
transform: none|transform-functions|initial|inherit;
```

## Animation
### Usage
```
@keyframe myName {
    from { color: blue; }
    to { color: red; }
}
@keyframe myName {
    0% { color: blue; }
    50% { color: red; }
    100% { color: yellow; }
}

animation: name duration timing-function delay iteration-count direction fill-mode play-state;
```
### Animation Properties
* `animation-name`
* `animation-duration`
* `animation-timing-function`
* `animation-delay`
* `animation-iteration-count`
* `animation-direction`
    * `normal` Normal animation
    * `reverse` Animation move from `to` to `from`
    * `alternate` Animation move from `from` to `to` and then go back.
    * `alternate-reverse` Same as alternate but starts from `to`.