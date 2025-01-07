---
title: Review and Destroy
module: 11
jotted: false
---

# Review
<div class="tab">
  <button class="tablinks active" onclick="openTab(event, 'Overview')">Overview</button>
  <button class="tablinks" onclick="openTab(event, 'destroy')">destroy</button>
  <button class="tablinks" onclick="openTab(event, 'remove')">remove</button>
   <button class="tablinks" onclick="openTab(event, 'video')">Video</button>
</div>

<div id="Overview" class="tabcontent" style="display:block"  >
<div class="tabhtml" markdown="1">

At this point, your code displays an animation and an immovable object. The character is unable to move through the object.  In addition, we added an attack animation.  We are still using the p5.play library to display the animations and the object.

```js

var idlePaths = [];
var myAnimation;
var myWalkAnimation;
var walkPaths = [];
var attackPaths = [];
var catImage;

function preload() {
    idlePaths = loadStrings("./images/idle/idle.txt");
    walkPaths = loadStrings("./images/walk/walk.txt");
    attackPaths = loadStrings("./images/attack/attack.txt");
}

function setup() {
    createCanvas(800, 600);
    myAnimation = new animationImage(200, 200, 150, 150);
    myAnimation.loadAnimation('idle', idlePaths);
    myAnimation.loadAnimation('walk', walkPaths);
    myAnimation.loadAnimation('attack', attackPaths);

    //compact way to add an image
    catImage = createSprite(450, 200, 100, 100, 'static');
    catImage.img = "./images/cat.jpg";
    catImage.scale = 0.05;
    catImage.diameter = 150;

}

// display all the frames using the draw function as a loop
function draw() {

    background(120);

    if (kb.pressing('d')) {
        myAnimation.updatePosition('forward');
        myAnimation.drawAnimation('walk');
        if (myAnimation.isColliding(catImage)) {
            myAnimation.drawAnimation('idle');
            myAnimation.updatePosition('idle');

        }
    }
    else if (kb.pressing('a')) {
        myAnimation.updatePosition('reverse');
        myAnimation.drawAnimation('walk');
    }
    else if (kb.pressing('x')) {
        myAnimation.drawAnimation('attack');
    }
    else {
        myAnimation.drawAnimation('idle');
    }

    catImage.debug = mouseIsPressed;

}

```

At the moment, I can move the character to the left and right and attack. It also places an object on the screen. However, how do we destroy the object when it is attacked?  Eventually we are going to integrate the particle system, but for now, let's just remove it.

</div>
</div>

<div id="destroy" class="tabcontent">
<div class="tabhtml" markdown="1">

### Destroy

The code that is most important is the attack.

```js
    else if (kb.pressing('x')) {
        myAnimation.drawAnimation('attack');
    }
```

With the p5 play library and the p5.js library, we can get all the information we need.

We are going to use the `dist` function to determine if we are close enough to destroy the object.

So, the code will look like this now.

```js
    else if (kb.pressing('x')) {
        myAnimation.drawAnimation('attack');
        if (dist(myAnimation.getCurrentAnimation().position.x, myAnimation.getCurrentAnimation().position.y, catImage.position.x, catImage.position.y) < 200) {
            console.log("destroy");
        }
    }
```

The `dist` function needs two points the first point (x,y) will be the location of the character.  The second point (x,y) will be the obstacle.  I am checking to see if it's less than 250 pixels away. If it is, then destroy it.  This may vary for you.

At the moment, I am just printing out **destroy**.  Not very intimating.  How do I remove it?

</div>
</div>

<div id="remove" class="tabcontent">
<div class="tabhtml" markdown="1">


#### remove

We are going to use the `remove` function in p5.js.  If you use the **remove** without any other parameters, the whole sketch will be removed. However, we can use the dot operator to remove just one item. In this case, the obstacle.

So, now our code will look like this.

```js
  if (dist(myAnimation.getCurrentAnimation().position.x, myAnimation.getCurrentAnimation().position.y, catImage.position.x, catImage.position.y) < 200) {

      catImage.remove();
      catImage = null;
  }
```

Now, when the `x` key is pressed, if the character is close enough to the obstacle, it will disappear and the reference to the obstacle is set to nothing so a reference error will appear.  We will have to change a few other sections too though. We must check to make sure the cat is not null whenever we evaluate collision. The entire section will look like this now.

```js

function draw() {

    background(120);

    if (kb.pressing('d')) {
        myAnimation.updatePosition('forward');
        myAnimation.drawAnimation('walk');
        if (catImage != null) {
            if (myAnimation.isColliding(catImage)) {
                myAnimation.drawAnimation('idle');
                myAnimation.updatePosition('idle');

            }
        }
    }
    else if (kb.pressing('a')) {
        myAnimation.updatePosition('reverse');
        myAnimation.drawAnimation('walk');
    }
    else if (kb.pressing('x')) {
        myAnimation.drawAnimation('attack');
        if (catImage != null) {
            if (dist(myAnimation.getCurrentAnimation().position.x, myAnimation.getCurrentAnimation().position.y, catImage.position.x, catImage.position.y) < 200) {

                catImage.remove();
                catImage = null;
            }

        }
    }
    else {
        myAnimation.drawAnimation('idle');
    }
}
```

Pretty cool right?  How do we integrate our particle system?

</div>
</div>
<div id="video" class="tabcontent">
<div class="tabhtml" markdown="1">

<iframe width="560" height="315" src="https://www.youtube.com/embed/74z9MO1lBjQ" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

</div>
</div>
