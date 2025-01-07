---
title: Directory Structure
module: 4
jotted: true
---

# Directory Structure

It's good to think about how to set up our directory structure to make sure we keep all our files organized.  At first, it's okay to have just our html file and our .js file. However, as we add more files, it's good to organize them and know how to access them.

## Images folder

In p5.js, we can create any folder structure we want. It's good to have folders that match what files are inside.  For instance, if we have an **images** folder, we should contain files that have a .jpg, .png, or .gif extension.

# JS folder

As we add more custom p5.js files, we want to keep them organized and separate from our third-party libraries.  In a folder called **js**, we can organize our JavaScript files here.

## Libs folder

As we continue with our journey, having a folder that contains all the external or third-party libraries can be useful.  For instance, our **p5.min.js** file can go in this folder as well as the play library, the sound library and many others.

There are many other folders than you can create to keep things organized for the long-term.

Below is an example of what the directory structure could look like.

```
HW-3
├── images/
│   ├── picture.jpg
│   ├── picture2.jpg
│   └── picture3.jpg
├── index.html
└── js
|   └──sketch.js
└── libs
|   └──p5.min.js
```

So, how does one access a file that is in the assets folder?  Go to the next section to find out.
