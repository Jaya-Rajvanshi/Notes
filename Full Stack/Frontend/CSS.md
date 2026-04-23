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

## CSS Pseudo-Classes

```
.subscribe-button{      /These styles only apply when hovering over an         ....                 /element with class="subscribe-button"
}

.subscribe-button:active{      /These styles only apply when clicking on an         ....                   /element with class="subscribe-button"
}
```

## Intermediate CSS Properties

```
.subscribe-button{
    opacity: 0.5;                       /Sets how see-through an element is: 0.5 = 50% see-through
    opacity: 0;                         /0 = complete see-through (invisible).
    opacity: 1;                         /1 = not see-through (this is the default value).
    
    transition: <property> <duration>;   /Transition smoothly when changing styles (often used when hovering).
    transition: background-color 1s;     /Transition background color over 1s.
    transition: color 0.15s;             /Transition text color over 0.15 s.
    transition: <property1> <duration1>, /Transition multiple properties  
     <property2> <duration2>,            /by separating them with a comma.
     ...;
    transition: background-color 0.15s,   /Transition both background color and text color over 0.15 s.
      color 0.15s;                       
    box-shadow: <h-position> <v-position> <blur> <shadow>;
    box-shadow: 3px 4px 5px black;             /Creates a shadow that's 3px to the right of the element, 4px to the bottom, with 5px of blur and color of black.
    box-shadow: 3px 4px 0 rgba(0, 0, 0, 0.15);       /Creates a shadow that's 3px to the right, 4px to the bottom, with no blur, and a very faint black color.
 }
```

## Chrome DevTools

Lets us view (and modify) the HTML and CSS of a website directly in the browser. To open the DevTools: right-click > Inspect.

## CSS Box Model

● Determines how much space an element takes up. 
● Determines how far away elements are from each other.


```
.join-button { 
margin-right: 10px;      /Add 10px of space on the outside of the element.
margin-left: 10px;    
margin-top: 10px;
margin-bottom: 10px;     /Normal margin pushes things away from an element
margin-right: -20px;     /Negative margin pulls things towards an element 

margin: 10px;            /Shorthand for adding 10px of margin on all sides. 
margin: 10px 20px;       /Add 10px of margin top & bottom and 20px left & right margin: <top> <left & right> <bottom>; 
margin: <top> <right> <bottom> <left>;

padding-right: 10px;      /Add 10px of space on the inside of the element. 
padding-left: 10px; 
padding-top: 10px; 
padding-bottom: 10px; 
padding-right: -20px;     /Negative padding has no effect.

border-width: 1px;                /Sets the border width. 
border-style: solid;              /Sets the border style (to a solid color). 
border-color: red;                /Sets the border color.

border: <width> <style> <color>;  /Shorthand for the above 3 properties.
border: 1px solid red; 
```

## Text Styles

```
.title { 
font-family: Arial;                     /Change the font.
font-family: Roboto, Verdana, Arial;    /A font-stack: if Roboto is not available, it will fall back to Verdana. If Verdana is not available it will fall back to                                          /Arial.
font-size: 30px;                     /Change text size.
font-weight: bold;                   /Change text thickness
font-weight: 700;                    /Another way to specify font-weight. We can use: 100, 200, 300, ..., 900. bold = 700, regular = 400, semibold =500
font-style: italic;                  
text-align: center;                  /Other values we can use: left, right, justified
line-height: 24px;                   /Adjust space between lines of text.
text-decoration: underline;          /Underlines the text.
text-decoration: none;               /Removes underline.

```

< p > by default have margin-top and margin-bottom. A common practice is to:
1. Reset the default margins
   
```
p { 
margin-top: 0; 
margin-bottom: 0; 
}
```

2. Then apply more precise margins.
```
.title { 
margin-bottom: 16px; 
}
```

### Text Element (Also called Inline Elements)

● Text elements (< strong>, < u>, < span>, < a>) appear within a line of text.
```
<p>
This is a <strong> text element </strong>
</p>
```
Useful if we want to style only a part of the text. 

●  < span >is the most generic text element (it doesn't have any default styles). 
● We can style text elements using a class:

```
<p>
This is a <span class = "shop-link"> text element </span>
</p>

.shop-link { 
text-decoration: underline; 
}
```

## The HTML Structure

```
<!DOCTYPE html>  /Tells the browser to use a modern version of HTML.
<html>
<head>           /contains everything that's not visible like the title and description (a.k.a. metadata) as well as links to fonts and CSS stylesheets.
<body>
...              /contains everything that's visible like buttons, text, images, etc
</body>
</head>
</html>
