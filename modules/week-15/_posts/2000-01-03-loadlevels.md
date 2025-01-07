---
title: Load Levels
module: 15
---


## Levels  

Now that you know how to interact with the if/then scripts in Unity Playground, let's load different levels.

### Create a Load Scene

1. In the Project tab, find the ***Scenes*** folder.
2. Right-click the Scenes folder and select ***Create***.
3. Scroll until you find ***New Scene***.
4. Rename the scene, ***Loading***.

### Add the components

1. Add a background.
2. Add a movable object. (add the RigidBody 2D, Collision 2D of your choice and the Move script)
3. Add an object that the movable object can collide into. (add the Collision 2D of your choice) - tag it as the ***Pick up***

### Add the if/then statements

1. Navigate to the Scripts folder.
2. Expand the ***Conditions*** folder.
3. Drag the ***ConditionCollision*** script into the Inspector of the movable object.
4. In the Actions folder, drag the ***LoadLevelAction*** script into the Inspector of the movable object.
5. In the Inspector, make sure the Condition Collision filters by tag, select Pick up.
6. Under Gameplay Actions, click the ***+*** and select LoadLevel Action.
7. Under the Load Level, select Level 1 (or whatever your main scene is called) - if this level doesn't show, go to the next section first.

### Make sure all scenes are part of the project.

1. To move from level to level, all scenes must be part of the project.
2. Open the scene you want to add.
3. Select File -> Build Settings.
4. Click ***Add Open Scenes***.

### Test it!

Click Run and see if the level changes.