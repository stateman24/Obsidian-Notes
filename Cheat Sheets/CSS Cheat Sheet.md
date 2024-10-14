# Border
To give an element border
```css
p {
	border: 1px solid green
}
```

# Pseudo-class selector
`:last-of-type` is used to select the last element of a specific type of tag


```css
.inline {
	width: unset; \* it is used to set the width of the element to zero (I think ) *\ 
}
```
To align vertically I can use the `vertial align` property


#  Flexbox
The `flex-wrap` property determines how your flex items behave when the flex container is too small. Setting it to `wrap` will allow the items to wrap to the next row or column. `nowrap` (default) will prevent your items from wrapping and shrink them if needed.

The `justify-content` property determines how the items inside a flex container are positioned along the main axis, affecting their position and the space around them.

The `align-items` property positions the flex content along the cross axis. In this case, with your `flex-direction` set to `row`, your cross axis would be vertical.

The `gap` CSS shorthand property sets the gaps, also known as gutters, between rows and columns. The `gap` property and its `row-gap` and `column-gap` sub-properties provide this functionality for flex, grid, and multi-column layout. You apply the property to the container element.