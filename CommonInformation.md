## Common information ##
You can create  Horizontal and Vertical Sliderbars. Each SliderBar consists of a set of elements. Elements are shown on picture below. You can create elements and design SliderBars on base of this elements.

![https://lh4.googleusercontent.com/_uimY4ZD7jQU/TVWqFDTC8ZI/AAAAAAAAAdM/B2q9Xa9mLec/SliderBarCommon.png](https://lh4.googleusercontent.com/_uimY4ZD7jQU/TVWqFDTC8ZI/AAAAAAAAAdM/B2q9Xa9mLec/SliderBarCommon.png)

Scale and drag (knob) are required components of SliderBar. SliderBar  may include only one drag element and only one scale element. SliderBar may include zero or more 'less' and 'more' elements. See examples below.

_**Example 1**_

![https://lh3.googleusercontent.com/_uimY4ZD7jQU/TVWq-LwpgdI/AAAAAAAAAdU/dWppu8Mv-zE/scaledrag.png](https://lh3.googleusercontent.com/_uimY4ZD7jQU/TVWq-LwpgdI/AAAAAAAAAdU/dWppu8Mv-zE/scaledrag.png)

SliderBar on picture above consists only of scale and drag (knob) elements (without 'more' or 'less' elements).

_**Example 2**_

![https://lh4.googleusercontent.com/_uimY4ZD7jQU/TVWrr8Yrg1I/AAAAAAAAAdc/H3xBjnBfWeo/twomore.png](https://lh4.googleusercontent.com/_uimY4ZD7jQU/TVWrr8Yrg1I/AAAAAAAAAdc/H3xBjnBfWeo/twomore.png)

SliderBar on picture above includes two 'more' elements and one 'less' element (except scale and drag).

### Requirements for elements ###

Less element, More element, Scale element and Drag element are common GWT widgets (descendant of Widget class). This widgets must implement following interfaces:

| **Widget** | **Interfaces** |
|:-----------|:---------------|
| Less widget | HasMouseDownHandlers |
| More widget | HasMouseDownHandlers |
| Scale widget | HasMouseDownHandlers |
| Drag widget | HasMouseDownHandlers, HasMouseUpHandlers, HasMouseMoveHandlers |

### Common approaches to the use of SliderBar ###

Some integer value corresponds to each position of Drag element. Zero corresponds to leftmost position of horizontal SliderBar or topmost position of vertical SliderBar. Value which corresponds to rightmost position of Drag widget of horizontal SliderBar (or bottommost position of vertical SliderBar) is defined by User.

![https://lh6.googleusercontent.com/_uimY4ZD7jQU/TVY1afnKhLI/AAAAAAAAAd8/_YjYZPLVOHw/dragvalue.png](https://lh6.googleusercontent.com/_uimY4ZD7jQU/TVY1afnKhLI/AAAAAAAAAd8/_YjYZPLVOHw/dragvalue.png)

On above picture we can see which values correspond to different Drag widget position for horizontal SliderBar (User sets max value to 7).

It is possible to interract with scrollbars by all availabble means:

  1. drag knob
  1. clic mouse on scale or on scale arrows
  1. use arrow keys on clipboard
  1. use mouse wheel

When position of knob is changed 'BarValueChangedEvent' is fired. You cen react to this event by adding 'BarValueChangedHandler'  hasndler to SliderBar.