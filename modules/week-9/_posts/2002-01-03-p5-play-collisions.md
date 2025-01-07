---
title: p5.play collisions 
module: 9
jotted: false
---

# Collisions in p5.play

<a href="https://youtu.be/qRK9e1fq634" target="_blank">Video</a>

So, how do we deal with collisions?  In  p5.play, they have a built-in collision function.

First, let's add a new image.

```js

var idlePaths = [];
var myAnimation;
var myWalkAnimation;
var walkPaths = [];
var catImage;

function preload() {
   idlePaths = loadStrings("./images/idle/idle.txt");
   walkPaths = loadStrings("./images/walk/walk.txt");
 
}

function setup() {
  createCanvas(800,600);
  myAnimation = new animationImage( 200, 200, 150, 150);
  myAnimation.loadAnimation('idle', idlePaths);
  myAnimation.loadAnimation('walk', walkPaths);
  //compact way to add an image
  catImage = createSprite(450, 200);
  catImage.scale = .05;
  catImage.addImage(loadImage('./images/cat.jpg'));


}

// display all the frames using the draw function as a loop
function draw() 
{

    background(120);
    
    if(kb.pressing('d'))
    {
        myAnimation.updatePosition('forward');
        myAnimation.drawAnimation('walk');         
    }
    else if(kb.pressing('a'))
    {
        myAnimation.updatePosition('reverse');
        myAnimation.drawAnimation('walk');        
    }
    else
    {
        myAnimation.drawAnimation('idle');
    } 
}

```

However, if we move, we will walk right through the rock. That won't work!

So, what will we do?  We can use the `collide` function and that will check to see if two objects have collided.

```js
ar idlePaths = [];
var myAnimation;
var myWalkAnimation;
var walkPaths = [];
var catImage;

function preload() {
   idlePaths = loadStrings("./images/idle/idle.txt");
   walkPaths = loadStrings("./images/walk/walk.txt");
   
}

function setup() {
  createCanvas(800,600);
  myAnimation = new animationImage( 200, 200, 150, 150);
  myAnimation.loadAnimation('idle', idlePaths);
  myAnimation.loadAnimation('walk', walkPaths);

  //compact way to add an image
  catImage = createSprite(450, 200,100,100, 'static');
  catImage.img = "./images/cat.jpg";
  catImage.scale = 0.05;
  catImage.diameter = 150;
  
 

}

// display all the frames using the draw function as a loop
function draw() 
{

    background(120);
    
    if(kb.pressing('d'))
    {
        myAnimation.updatePosition('forward');
        myAnimation.drawAnimation('walk');    
        if(myAnimation.isColliding(catImage))
        {
            myAnimation.drawAnimation('idle');
            myAnimation.updatePosition('idle');
            
        }     
    }
    else if(kb.pressing('a'))
    {
        myAnimation.updatePosition('reverse');
        myAnimation.drawAnimation('walk');        
    }
    else
    {
        myAnimation.drawAnimation('idle');
    } 

    catImage.debug = mouseIsPressed;

}

```

And we can update the animationImage's isColliding to look like this.

```js

 isColliding(myImage) {
        return this.currentAnimation.collide(myImage);
    }

```

<a href="https://github.com/Montana-Media-Arts/220_CreativeCoding2-Spring2023-Samples/blob/main/Week%208/p5play%20collisions.zip" target="_blank">Example</a>

**Note** We also added the debug at the bottom so we can see the bounding boxes on the sprites.  This will tell us where they are colliding.  Now, I am going to let you know work with the play library.