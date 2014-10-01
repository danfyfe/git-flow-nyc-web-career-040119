---
languages: bash, git
tags: git, merge, pull, fetch, commit, pull, push, wip
resources: 5
---

# Git Flow

## Objectives

* Get familiar with git syntax
* Get comfortable creating, merging, pushing, and pulling branches.
* Resolve merge conflicts

## Instructions

Remember to fork and clone this lab if you haven't already.

### Branching

Before altering your code base, open `index.html` in the browser. In the first part of this lab, you're going to add a photo of a turtle below the image of the tree.

* Type `git branch`. This should return master.
* Make a new branch called `add-turtle` from the master branch: `git branch add-turtle`
* Type `git branch` again. Now you should see `master` (highlighted) and `add-turtle` 
* Switch to the turtle branch: `git checkout add-turtle`
* Make sure you switched successfully by typing `git branch` again. This should return `master` and `add-turtle` (highlighted).
* In `index.html`, below the tree picture and caption section, add the turtle picture using the HTML below:

```HTML
<!-- begin turtle picture and caption -->
<div class="center-container">
  <div class="card">
    <div class="caption">
      <h4>From the Sky</h4>
      <p>Montse Grillo</p>
      <p>Tenerife, Canary Islands</p>
    </div>
  </div>
  <div class="card">
    <img src="public/img/turtle.jpg" alt="sea turtle swimming">
  </div>
</div>
<!-- end turtle picture and caption -->
```

* Open up your `index.html` and see how the page looks.
* Stage and commit your changes.

### Merging

Now that you've sucessfully added a turtle pic and caption to the add-turtle branch, you're going to merge that branch into master.

* The first step is to switch back to the master branch: `git checkout master`
* Now you're going to merge the add-turtle branch in: `git merge add-turtle`
* Open up your `index.html` in the browser. How does it look? Does it have two pictures now? 

While you have this change locally, your remote repo still thinks that `index.html` just has one picture, the tree/bird one. You need to tell about this update.
* Push the update to your master branch on your remote repo: `git push origin master`
* To make sure this push worked, visit your fork of this repo. From there, you can double check in at least two ways: 
  1. There will be a light blue bar above the file struture of the repo:
  ![blue bar](/img/blue-bar.png) that displays the most recent commit. This bar should have your GitHub picture followed by your GitHub name and a time stamp.
  2. Click on ![num of commits](/img/commits.png). The most recent commit, the one at the top, should be the one you made.

* Let's get local again: How many branches do you expect to see when you type `git branch`? How many are there? What does this tell you about merging?

### Deleting A Local Branch

Now that you've added the changes you've made from add-turtle to master, and master has been pushed to the remote repo successfully, it's time to delete your local version of add-turtle.

* Make sure you're on master: `git branch` should return `master` highlighted.
* Type `git branch -d add-turtle`
* To make sure this branch was sucessfully deleted, type `git branch`. You should only see `master` now.

### Creating a Merge Conflict

#### Walrus Branch

From master, make a new branch, add-walrus. On this branch, you're going to add the below code to `index.html`, under the tree picture.

```HTML
<!-- begin walrus picture and caption -->
<div class="center-container">
  <div class="card">
    <div class="caption">
      <h4>Hello</h4>
      <p>Misty Gage</p>
      <p>Point Defiance Zoo, Tacoma, WA</p>
    </div>
  </div>
  <div class="card">
    <img src="public/img/walrus.jpg" alt="walrus swimming with bubbles">
  </div>
</div>
<!-- end walrus picture and caption -->
```
Remember to add and commit these changes.

#### Polar Bear Branch

From the walrus branch, switch to master. From master, make a new branch, add-walrus-and-polar-bear. On this branch, you're going to add the below code to `index.html`, under the tree picture (the same location where you added the walrus photo).

```HTML
<!-- begin polar bear picture and caption -->
<div class="center-container">
  <div class="card">
    <img src="public/img/polar-bear.jpg" alt="walrus swimming with bubbles">
  </div>
  <div class="card">
    <div class="caption">
      <h4>Arctic Hi Five</h4>
      <p>Colin Mackenzie</p>
      <p>Svalbard, northern Norway</p>
    </div>
  </div>
</div>
<!-- end polar bear picture and caption -->
```
Remember to add and commit these changes as well.

#### Merging with Conflicts

* From the add-walrus-and-polar-bear branch, merge the add-walrus branch: `git merge add-walrus`
* Fix the merge conflict in `index.html` so that index now has three photos: tree, walrus, and polar bear.
* Add and commit these changes.

#### Pushing a Local Branch

Now you're going to create a `add-walrus-and-polar-bear` branch on your remote repo.

* From the branch `add-walrus-and-polar-bear`, push the code to a remote branch of the same title. You can do this in one line with: `git push origin add-walrus-and-polar-bear`. 

* To ensure this push worked, head over to GitHub and view your forked repo. Click on the branch dropdown: ![branch dropdown](/img/branch-dropdown.png), there should be the option to view the `add-walrus-and-polar-bear` branch.
* Now your master branch has a tree and a turtle while add-walrus-and-polar-bear has tree, walrus, and polar bear.
* Since you merged add-walrus into add-walrus-and-polar-bear, go ahead and delete it. Remember that you cannot "be" on the branch that you're trying to delete so make sure you're on master or add-walrus-and-polar-bear instead.

### Getting a Remote Branch

Many times when working in groups, a developer will branch off of master, in this example let's call this branch "change-color-scheme", add some code, then push this new branch to the remote repo for another developer to work on. 

#### Lauren Time

Since you're working on this project alone, you're going to mimic the remote creation of a new branch. You're going to pretend to be a team member for this section. This team member you will pretend to be is named Lauren and Lauren loves to add designs and stuff to readmes.

* The first step is to pretend to be Lauren.
* As Lauren, create a new branch called "add-fireflies" in your git-flow repository on Github using the pictured interface:
  * ![branch dropdown](/img/branch-dropdown.png)
* Type "add-fireflies" then click on "Create branch: add-fireflies from 'master'", as pictured below:
![firefly branch](/img/firefly-branch.png)
* This will redirect you to a newly created branch on your remote repo called "add-fireflies". From here, click on `README.md`:
  * ![readme](/img/readme-link.png)
* Now click on the pencil icon, shown below:
  * ![edit icon](/img/edit.png)
* Near the top of the markup, below the "Objectives" section, add the text below:

```text

## Lauren Here:
  ____  _    _  _____  _____ 
 |  _ \| |  | |/ ____|/ ____|
 | |_) | |  | | |  __| (___  
 |  _ <| |  | | | |_ |\___ \ 
 | |_) | |__| | |__| |____) |
 |____/ \____/ \_____|_____/                                                                                               
```
* Now the readme should look like this:
  * ![bugs added to readme](laruen.png)

* Scroll to the bottom, add a commit message like "added bugs to readme", and click commit changes.
  * ![commit changes](/img/commit-changes.png)
* Lauren's work here is done. You can go back to being you.

#### You Time

Now you need to get the changes that Lauren made.

* The first step is to 


## Resources
* [SourceTree Blog](http://blog.sourcetreeapp.com/) - [Merge or Rebase?](http://blog.sourcetreeapp.com/2012/08/21/merge-or-rebase/)
* [Pro Git](http://git-scm.com/book/) - [Chapter 3 Git Branching](http://git-scm.com/book/en/Git-Branching)
* [Pro Git](http://git-scm.com/book/) - [3.1 Git Branching - What a Branch Is](http://git-scm.com/book/en/Git-Branching-What-a-Branch-Is)
* [Pro Git](http://git-scm.com/book/) - [3.2 Git Branching - Basic Branching and Merging](http://git-scm.com/book/en/Git-Branching-Basic-Branching-and-Merging)
* [LearnGitBranching](http://pcottle.github.io/learnGitBranching/) - [Introduction Sequence: Branching in Git](http://pcottle.github.io/learnGitBranching/)
