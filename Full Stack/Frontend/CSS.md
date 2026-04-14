Core Concepts
- What is CSS
- Selectors
- Specificity
- Box model
 Layout Systems
- display types
- flexbox
- grid
Responsive Design
- media queries
- units (%, rem, vw)
Advanced
- positioning
- z-index
- animations (if covered)

## CSS Basics

Stands for Cascading Style Sheets. Based on the name, it is used to style our webpages or change the appearance of our HTML elements.
One way of writing CSS code is using the < style > HTML element.

```
<style>                          
 button{                     Modifies all <button>s on the page
   background-color: red;    Change background color to red.
   color: white;             Change text color to white
   }
</style>
```


## CSS Properties

Here are some common CSS properties we can use:

```
button {
  background-color: red;  /Sets the background color. Common values:
                          ● Color name: red, white, black    ● rgb value: rgb(0, 150, 255);   ● Hex value: #0096FF
  color: white;           /Sets the text color. Takes the same values as background-color (color name, rgb, hex).
  height: 36px;           /Sets the height. Common values are:  ● Pixel value: 36px ● Percentage: 50%
  width: 105px;           /Sets the width. Takes the same value as height
  border: none;           /Removes the border
  border-radius: 2px;     /Creates rounded corners
  cursor: pointer;        /Changes the mouse/cursor when hovering over the 
                          element.
  border-color: red;      /Sets the border color.
  border-style: solid;    /Sets the border style. Common values: ● solid ● dotted ● dashed
  border-width: 1px;      /Sets the border width. 
  }
```


## How to Google CSS Properties

We regularly use Google to search for CSS properties that we don't know or don't remember. When using Google, search what you're trying to accomplish. Examples: 
"css rounded corners", "css text italic" ,"css adjust space between lines" and so on.

## CSS Values

Each CSS property has a set of values that are allowed (==background-color== allows color values, ==cursor== allows solid, dotted, dashed, etc.) Here are some categories of values that are useful to know:

**Color Values** 

1. A color name: red, white, black 
2. RGB value: rgb(0, 150, 255); RGB is a more precise way of measuring color. Every color can be created using a combination of red, green, and blue (RGB). In CSS, this is represented by rgb(...); Each color has a min value = 0 and a max value = 255. 
    rgb(0, 0, 0); = black  and  rgb(255, 255, 255); = white
3. Hex value Hex is another way to write RGB.
4. RGBA value: rgba(0, 150, 255, 0.5); Same as RGB, except with an additional a-value (alpha value). The a-value determines how see-through the color is. 0 = complete see-through, 1 = solid color and not see-through, 0.5 = 50% see-through.

**Measurement Values**

1. Pixels: 50px, 100px 
   Pixels (px) are a common unit of measurement in the digital world. For example: a 4K screen is 3840px by 2160px. 
2. Percent: 50%, 100% 
   A relative measurement. For example, width: 50%; means 50% of the width of the page (or if the element is inside another element, 50% of the width of the container element). 
3. em / rem: 1em, 1rem 
   Relative measurements that are useful for accessibility. em = relative to the font-size of the element (2em means 2 times the font size). rem = relative to the font-size of the page, which is 16px by default (2rem means 2 times the font size of the page = 2 * 16px = 32px by default).

## Class Attribute

Class attribute = lets us target specific elements with CSS.

```
<button class="subscribe-button">   /Add a class name to an element.
SUBSCRIBE                           /The class name can be anything we want
</button>                           /but no spaces allowed
.subscribe-button{
...}
```
Multiple elements can have the same class.

```
<button class ="youtube-button" "subscribe-button">
SUBSCRIBE
</button>
```
An element can have multiple classes separated by spaces. Also, elements can be targeted by multiple CSS selectors.

```
.button{                  /all 3 selectors will target the button above
..}
.youtube-button{
...}
.subscribe-button{
...}
```
