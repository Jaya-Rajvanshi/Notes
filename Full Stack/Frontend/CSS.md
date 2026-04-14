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

## CSS Syntax

![[Pasted image 20260414110845.png]]


## CSS Properties

Here are some common CSS properties we can use:

```
button {
  background-color: red;  /Sets the background color. Common values:                                    ● Color name: red, white, black                                             ● rgb value: rgb(0, 150, 255);                                              ● Hex value: #0096FF
  color: white;           /Sets the text color. Takes the same values as                               background-color (color name, rgb, hex).
  height: 36px;           /Sets the height. Common values are:                                          ● Pixel value: 36px ● Percentage: 50%
  width: 105px;           /Sets the width. Takes the same value as height
  border: none;           /Removes the border
  border-radius: 2px;     /Creates rounded corners
  cursor: pointer;        /Changes the mouse/cursor when hovering over the 
                          element.
  border-color: red;      /Sets the border color.                              border-style: solid;   /Sets the border style.                                                      Common values: ● solid ● dotted ● dashed            border-width: 1px;     /Sets the border width. 
  }

