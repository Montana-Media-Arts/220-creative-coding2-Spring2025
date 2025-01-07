---
title: p5.play keyboard 
module: 9
jotted: false
---

# Using the keyboard in p5.play

<a href="https://youtu.be/tHpKdgUMm3U" target="_blank">Video</a>

So, in order to make an animation change, we have to create two different animations and then move along the x or y axis just like before.  So, let's add onto what we started with.  We also need to update the **animationImage** class and its constructor.

The new animationImage class constructor should look like this. Notice the fileNames is no longer present.  Where did it go?

```js
 constructor( x, y, w, h)
    {
        this.x = x;
        this.y = y;
        this.w = w;
        this.h = h;
        this.imageObjects = [];
        this.currentAnimation;
        this.createAnimation(); // new function
        this.i = 0;
        this.currentFrameCount = 0;
        this.direction  = "";      
    }

```

We must create a new function to create an animation and then load the different animation types.
The createSprite function the p5play library allows us to have different animation types (i.e. idle and walk)

```js

createAnimation()
{
    this.currentAnimation = createSprite(300, 250);
}

```

```js

loadAnimation(animationType,fileNames)
{ 
    this.currentAnimation.addAnimation(animationType,fileNames[0], fileNames[fileNames.length-1]);
       
}

```
This function allows us to set different animation types for the sprite. 

And the drawAnimation function calls the displays the different animation depending on the animation type sent to the function.

```js

drawAnimation(animationType)
{  
   this.currentAnimation.frameDelay = 5; 
   this.currentAnimation.changeAnimation(animationType);         
}

```

So, how do we call the different animation types? In the main sketch, we can call all these functions in the class like this.

```js

var idlePaths = [];
var myAnimation;
var myWalkAnimation;
var walkPaths = [];

function preload() {
   idlePaths = loadStrings("./images/idle/idle.txt");
   walkPaths = loadStrings("./images/walk/walk.txt");
}

function setup() {
  createCanvas(800,600);
  myAnimation = new animationImage( 0, 0, 150, 150);
  myAnimation.loadAnimation('idle', idlePaths);
  myAnimation.loadAnimation('walk', walkPaths);


}

// display all the frames using the draw function as a loop
function draw() 
{

    background(120);
    if(keyIsPressed)
    {
        if(key == 'd')
        {
            myAnimation.drawAnimation('walk');
        }
        else
        {
            myAnimation.drawAnimation('idle');
        }
    }
    else
    {
        myAnimation.drawAnimation('idle');
    }   
}

```

<a href="https://github.com/Montana-Media-Arts/220_CreativeCoding2-Spring2023-Samples/blob/main/Week%208/Change%20Animations%20example.zip" target="_blank"> Example</a>


<a href="https://youtu.be/61hEdXTZHWo" target="_blank">Video</a>

Now, how do we make it move while we walk?  First, we let's use the p5play keyboard events.

```js

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

Then, let's update our animationImage one more time to account for movement.

```js

drawAnimation(animationType) {
        
        this.currentAnimation.frameDelay = 5;
        this.currentAnimation.scale = .5;
        this.currentAnimation.changeAnimation(animationType);
        if (animationType == 'walk' && this.direction == 'forward') {
            this.currentAnimation.direction = 0;
            this.currentAnimation.mirror.x = false;
            this.currentAnimation.speed = 1;

        }
        else if (animationType == 'walk' && this.direction == 'reverse') {

            this.currentAnimation.mirror.x = true;
            this.currentAnimation.direction = 180;
            this.currentAnimation.speed = 1;

        }
        else {
            this.currentAnimation.velocity.x = 0;
        }


    }

```

<a href="https://github.com/Montana-Media-Arts/220_CreativeCoding2-Spring2023-Samples/blob/main/Week%208/Change%20Direction%20example.zip" target="_blank">Example</a>

We set the velocity back to 0.  Whew. that's better!  What about collisions?

