---
title: Collide2D library
module: 8
---

# p5.collide2d <br />


<br />


<div class="tab">
  <button class="tablinks active" onclick="openTab(event, 'Overview')">Overview</button>
  <button class="tablinks" onclick="openTab(event, 'Including')">Including the Library</button>
   <button class="tablinks" onclick="openTab(event, 'Collision')">Collision</button>
   <button class="tablinks" onclick="openTab(event, 'Videos')">Videos</button>
  <button class="tablinks" onclick="openTab(event, 'ToDo')">To Do</button>
 
</div>

<div id="Overview" class="tabcontent" style="display:block"  >
<div class="tabhtml" markdown="1">

In the previous section, basic collision was examined.  Ben Moran also created a library to help with 2D collision.


</div>
</div>

<div id="Including" class="tabcontent">
<div class="tabhtml" markdown="1">

Just like the base p5 library, the collision library can be added by CDN or by including it locally.

```html

<script defer src="https://unpkg.com/p5.collide2d"></script>

```
**or**

```html

<script src="./libs/p5.collide2d.min.js"></script>

```



</div>
</div>

<div id="Collision" class="tabcontent">
<div class="tabhtml" markdown="1">

If we use the same objects, we can use the new library function call to evaluate collsion.

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
  
  text(collideRectRect(r1.getX(), r1.getY(), r1.getW(), r1.getH(),r2.getX(), r2.getY(), r2.getW(), r2.getH()), 300,300);
 
}

```

</div>
</div>


<div id="Videos" class="tabcontent">
<div class="tabhtml" markdown="1">

* <a href="https://youtu.be/9WVone3FOFU" target="_blank">Basic Collision with a library</a>
* <a href="https://youtu.be/KwYiESraSx4" target="_blank">Library Collision with Animations</a>
</div>
</div>


<div id="ToDo" class="tabcontent">
<div class="tabhtml" markdown="1">
Try the code in the earlier tabs to see the final result. Feel free to change values.

<iframe src="https://editor.p5js.org/" width="100%" height="800px"></iframe>
</div>
</div>

