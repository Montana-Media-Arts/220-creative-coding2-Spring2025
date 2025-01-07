---
title: Applying p5.play
module: 9
jotted: false
---

# Applying p5.play

<a href="https://youtu.be/PHpPk5Fz2FI" target="_blank">Video</a>

So, let's look at what we did.

```js
var idlePaths = [];
var myAnimation;

function preload() {
   idlePaths = loadStrings("./images/idle/idle.txt");
}

function setup() {
  createCanvas(800,600);
  myAnimation = new animationImage(idlePaths, 0, 0, 150, 150);
 

}

// display all the frames using the draw function as a loop
function draw() 
{

    background(120);
    myAnimation.updatePosition('idle');
    myAnimation.setCurrentFrameCount(frameCount);
    myAnimation.drawAnimation();
}

```

This hopefully didn't seem like too big a deal at the time right?

What would it look like in p5.play?

We would need to go into the animationImage class and make some changes in the **loadAnimation** function and the **drawAnimation**

Here are the original functions. 

```js

 loadAnimation()
    {
        for(var i = 0; i < this.fileNames.length; i++)
        {
            this.imageObjects[i] = loadImage(this.fileNames[i]);
        }
         
    }

  drawAnimation()
    {  
        this.incrementIndex();
        if(this.direction == "reverse")
        {
            translate(this.w,0);
            scale(-1.0,1.0);
            image(this.imageObjects[this.i], -this.x, this.y, this.w, this.h);
        }
        else
        {
            image(this.imageObjects[this.i], this.x, this.y, this.w, this.h);
        }
        
           
        
    }

```

Here are the new functions.

```js

loadAnimation()
    {
         this.currentAnimation = loadAnimation(this.fileNames[0], this.fileNames[this.fileNames.length-1]);   
    }

  drawAnimation()
    {  
        this.currentAnimation.frameDelay = 5; 
        animation(this.currentAnimation, 300, 250);
    }

```


What just happened? We are still loading all the frames, but p5.play loads them all and infers the sequence by looking at the first image and the last image. Then we can use the **animation** function to display them.  The **frameDelay** slows down the animation for us.

<a href="https://github.com/Montana-Media-Arts/220_CreativeCoding2-Spring2023-Samples/blob/main/Week%208/Assets%20p5play%20example.zip" target="_blank">Example</a>

