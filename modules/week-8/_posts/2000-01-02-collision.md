---
title: Basic Collision Review
module: 8
---

# Basic Collision<br />


<br />


<div class="tab">
  <button class="tablinks active" onclick="openTab(event, 'Overview')">Overview</button>
  <button class="tablinks" onclick="openTab(event, 'Step1')">Step 1</button>
   <button class="tablinks" onclick="openTab(event, 'Step2')">Step 2</button>
    <button class="tablinks" onclick="openTab(event, 'Step3')">Step 3</button>
     <button class="tablinks" onclick="openTab(event, 'Step4')">Step 4</button>
     <button class="tablinks" onclick="openTab(event, 'Videos')">Videos</button>
  <button class="tablinks" onclick="openTab(event, 'ToDo')">To Do</button>
 
</div>

<div id="Overview" class="tabcontent" style="display:block"  >
<div class="tabhtml" markdown="1">

Collision has been covered over the last few weeks. Let's review.


</div>
</div>

<div id="Step1" class="tabcontent">
<div class="tabhtml" markdown="1">

Here is an example of basic collision where it looks at the bounding boxes of the two objects.

First, let's create a character class.

```js

class character
{
    constructor(path, x,y)
    {
        this.path = path;
        // need the image
        this.myImage = loadImage(this.path);
        this.x = x;
        this.y = y;
        this.imageWidth = 150;
        this.imageHeight = 200;
    }

    draw()
    {
        // image draw

        //rect(this.x,this.y, this.myImage.width, this.myImage.height);
        image(this.myImage, this.x, this.y, 150, 200);
    }

```



</div>
</div>

<div id="Step2" class="tabcontent">
<div class="tabhtml" markdown="1">

Then, we created food and animations

```js
// created animations
function preload() {

   
    for (var i = 0; i < 10; i++) {
        // concatenation - adding strings together
        myCharacter = new character("../images/Idle__00" + i + ".png", x, y);
        animation.push(myCharacter);
    }

   
}

// created food
function setup() {
    createCanvas(800, 800);
    setInterval(updateIndex, 50);
    for (let i = 0; i < 5; i++) {
        myFood = new food(random(100, 600), random(100, 600), 25);
        foodArray.push(myFood);
    }
}
 

```

</div>
</div>

<div id="Step3" class="tabcontent">
<div class="tabhtml" markdown="1">

Then, we created a function to see if the character was overlapping with another object.

```js

 hasCollided(x2, y2, w2, h2) {
        return (
          this.x < x2 + w2 &&
          this.x +  this.imageWidth > x2 &&
          this.y < y2 + h2 &&
          this.y + this.imageHeight > y2
        );
      }


```

</div>
</div>

<div id="Step4" class="tabcontent">
<div class="tabhtml" markdown="1">

So, then we checked after movement if the character had collided wit the food.

```js
 for (let k = 0; k < foodArray.length; k++) {
    if (animation[i].hasCollided(foodArray[k].x, foodArray[k].y, 25, 25)) {
        foodArray.splice(k, 1);       
    }
}

```

</div>
</div>

<div id="Videos" class="tabcontent">
<div class="tabhtml" markdown="1">
* <a href="https://youtu.be/4tyNBfWIlOc" target="_blank">Basic Collision with 2 rectangles</a>
* <a href="https://youtu.be/iomlnNsHCkA" target="_blank">Collision with Animations</a>
</div>
</div>



<div id="ToDo" class="tabcontent">
<div class="tabhtml" markdown="1">
Try the code in the earlier tabs to see the final result. Feel free to change values.

<iframe src="https://editor.p5js.org/" width="100%" height="800px"></iframe>
</div>
</div>

