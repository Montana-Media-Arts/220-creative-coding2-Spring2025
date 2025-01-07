---
title: Repositories with Multiple Collaborators
module: 2
jotted: false
---

<div class="tab">
    <button class="tablinks active" onclick="openTab(event, 'Overview')">Overview</button>
   
</div>

<div id="Overview" class="tabcontent" style="display:block" markdown="1">

**Create a New Repository to Collaborate with others**

Now that you know how to create a repository (or refresh your memories), we are going to learn how to connect with others.

In this section, you are to find at least **two** other people in the class and create a repository. One person will create the repository and then add the others as collaborators.

- Find the green "New repository" button and press it.

![new repo button on guthub.com](../imgs/Screen5.png)

- Give your repository a great name, like "_220-Collaboration_".
    - Optionally, give this repo a description, like "_This is how we share, Creative Coding 2 (MART220) course._".
- Keep this as a **public** repo.
- Select the **Initialize this repository with a README** box.
- Finally press the **Create Repository** button.

![Create repo window](../imgs/Screen6.png)

Your browser will now show you the brand new repository!

**Add Collaborators**

- Now, go to the Settings and click on _Collaborators_

![Click Collaborators](../imgs/Collaborators.png)

- Click **Add People** and search for the collaborators by GitHub username or email.

![Click Collaborators](../imgs/AddPeople.png)

- An email will be sent and the collaborator will need to accept.

**Pull from the repo and create content**

- Just as before, the all collaborators can use GitHub Desktop or any other Git pull to get the respository.
- However, instead of everyone pulling from main, each will create their own _branch_.

![Click Collaborators](../imgs/CreateBranch.png)

- Now, each user can pull the code and it will in their branch.
- Make sure you have chosen your branch in GitHub Desktop.

![Click Collaborators](../imgs/Branch.png)

- Next change the **ReadMe.md** file.  Add some text and push.

![Click Collaborators](../imgs/Changes.png)

- Next click **Preview Pull Request**

![Click Collaborators](../imgs/PreviewPull.png)

- Make sure the main branch is where you are merging into and then click **Create Pull Request**.

![Click Collaborators](../imgs/OpenPull.png)

- It should take you to GitHub.com and there you can click **Create Pull Reques**t.

![Click Collaborators](../imgs/GitHubPull.png)

- Because of the changes, the conflicts will need to be resolved by clicking on **resolve conflicts**.

![Click Collaborators](../imgs/ResolveConflicts.png)

- Remove all the conflicting markers.

![Alt text](../imgs/RemoveConflictMarkers.png)

- Then, click the **Mark as resolved** and then click **Commit merge**

![Alt text](../imgs/CommitMerge.png)

-  Now all changes have been updated to main and remember to **Pull Origin** to make sure all branches are up to date.


</div>