# Imersivo coding challenge
Coding challenge for Full Stack Engineer position.

## React
To run the React challenge,

```sh
npm install
npm run build # runs babel
npm run live  # runs localhost:3000
```

There are four components:
* App - Enclosing component.
* Square - Displays an array of items arranged into a square shape.
* Diamond - Displays an array of items arranged into a diamond shape.
* Subheading - Displays active shape.

### App

The app component houses the other three components as well as two buttons. Clicking on a button changes the state of App. This state is then used in the render function to determine which shape component should be rendered.

### Square

The Square component draws a square-like figure by laying out rows (`<div class=row>`) of items (`<div class=item>`) which are currently red circles. The items have assigned an animation to fade them in (`@keyframes fadeIn`) upon being attached to the DOM. To simulate that a square is progressively drawn, within its render method, each item is given an inline `animation-delay` based on its position.

The value of the last delay is then used to set a timeout for changing the subheading text. An extra second, 1000ms, is added to the delay since the animation to fade in an items lasts an additional second after the delay. The subheading's `setState()` function has been made available globally to allow for easy state setting (more on this in the Subheading's setion).

An IIFE is used to construct an array of rows, which in turn uses another IIFE to create an array of items. These arrays, being component arrays, render their elements in order.

The size of the square may be chosen by using a `size` attribute. The default size is 5. There is currently no input verification.

### Diamond

Works the same as `Square`, with different row-construction logic to produce the diamond shape.

The size of the diamond is the number of items in its middle row.

### Subheading

Displays the subheading, which is either `Current Shapes` or the shape being shown. Upon being mounted, its `setState()` function is made available in a global object, `gsub`. This global object is intended to store the name of the last shape the user requested be drawn as well as an id (in the form of a timestamp). This id is used in the function that is timed out within the shapes' render methods. The effect this has is to check whether the most recent shape requested (the most recent button clicked) is in fact the one that generated the very same timed-out function that is running. This is because the user could request a different shape before the current one is actually fully drawn on screen.

## Bootstrap
