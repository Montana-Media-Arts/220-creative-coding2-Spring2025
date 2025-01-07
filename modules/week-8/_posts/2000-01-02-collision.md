---
title: Week Collision
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

Collision is required game and for many interactive pieces. So, we will examine the basics of collision using box collision.


</div>
</div>

<div id="Step1" class="tabcontent">
<div class="tabhtml" markdown="1">

Here is an example of basic collision where it looks at the bounding boxes of the two objects.

First, let's create a Rectangle class.

```js

class Rectangle
{
  
  constructor(x,y,w,h)
  {
    this.x = x;
    this.y = y;
    this.w = w;
    this.h = h;
  }
  
  getX()
  {
    return this.x;
  }
  getY()
  {
    return this.y;
  }
  getW()
  {
    return this.w;
  }
  getH()
  {
    return this.h;
  }
  
  draw()
  {
    rect(this.x, this.y, this.w, this.h);
  }
}

```



</div>
</div>

<div id="Step2" class="tabcontent">
<div class="tabhtml" markdown="1">

Then, we need to create two Rectangle objects that can be evaluated.

```js

function setup() {
  createCanvas(400, 400);
}

function draw() {
  background(220);
  
  var r1 = new Rectangle(100,100,20,40);
  var r2 = new Rectangle(100,210,30,20);
  
  r1.draw();
  r2.draw();
  
 
}

```

</div>
</div>

<div id="Step3" class="tabcontent">
<div class="tabhtml" markdown="1">

We also need to a function to test if two objects are overlapping.  It might look something like this.

```js

function isRectanglesColliding(rec1, rec2){
    var topEdge1 = rec1.getY() + rec1.getH();
    var rightEdge1 = rec1.getX() + rec1.getW(); 
    var leftEdge1 = rec1.getX();
    var bottomEdge1 = rec1.getY();
    var topEdge2 = rec2.getY() + rec2.getH();
    var rightEdge2 = rec2.getX() + rec2.getW(); 
    var leftEdge2 = rec2.getX();
    var bottomEdge2 = rec2.getY();   
    
    if( leftEdge1 < rightEdge2 && rightEdge1 > leftEdge2 && bottomEdge1 < topEdge2 && topEdge1 > bottomEdge2){
        return true; 
   }
   return false;
}


```

</div>
</div>

<div id="Step4" class="tabcontent">
<div class="tabhtml" markdown="1">

Finally, we need to test if the two rectangles are overlapping one another.

```js

function setup() {
  createCanvas(400, 400);
}

function draw() {
  background(220);
  
  var r1 = new Rectangle(100,100,20,40);
  var r2 = new Rectangle(100,210,30,20);
  
  r1.draw();
  r2.draw();

  // this calls the function
  text(isRectanglesColliding(r1,r2), 300,300);
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

