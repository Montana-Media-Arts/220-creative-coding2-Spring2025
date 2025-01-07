---
title: Example
module: 9
jotted: false
---

# Example

<a href="https://youtu.be/j-2AMwfO6fs" target="_blank">Video</a>

So, what might an example look like and how do we break it down.

```html

<!DOCTYPE html>

<head>
    
    <script src="./libs/p5.min.js"></script>
    <script src="./libs/p5.collide2d.min.js"></script>
    <script src="./libs/p5.sound.js"></script>
    
    <!-- p5.play library using a CDN -->
    <script src="https://p5play.org/v3/planck.min.js"></script>
    <script src="https://p5play.org/v3/p5play.js"></script>
    
    <script src="./js/sketch.js"></script>
    
</head>

<body></body>

</html>

```

One simple example js file might be like this.

```js
//Creating animations

//animations like p5 images should be stored in variables
//in order to be displayed during the draw cycle
var ghost;

//it's advisable (but not necessary) to load the images in the preload function
//of your sketch otherwise they may appear with a little delay
function preload()
{
    ghost = loadAnimation('assets/wriggle01.png', 'assets/wriggle10.png');
}

function setup()
{
    createCanvas(800, 300);
}

function draw()
{
    background(255, 255, 255);

    animation(ghost, 300, 150);
}

```

<a href="https://github.com/Montana-Media-Arts/220_CreativeCoding2-Spring2023-Samples/blob/main/Week%208/Simple%20p5play%20example.zip" target="_blank">Download Example</a>

So, what happened here.

First, one variable are created to hold the animation.

```js
var ghost;
```

Then, the the animation is loaded by using a built-in function called `loadAnimation` in the preload function just like we did before when we loaded images.

```js

ghost = loadAnimation('assets/wriggle01.png', 'assets/wriggle10.png');


```

The setup function remains the same and then the draw function contains a function that displays the animation.

```js
  animation(ghost, 300, 150);
 
```

The animation is displayed in a specific x and y location.

How can we apply this to our example?
