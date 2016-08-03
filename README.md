<img align="right" src="01 Introduction to JavaScript/images/uni_logo.png">
.

.
#304CEM

Welcome to **Web API Development**. You are probably viewing this via **GitHub** so one of the first tasks we will be carrying out is showing you how to *clone* your own copy of the code and maintain it on *your own Git repository*.

Before we get started it is worth reiterating that the module covers some advanced programming concepts which you will be required to demonstrate in your assignment which is entirely assessed through a practical coursework assignment. The module comprises twelve topics, each containing three worksheets. You will spend all semester *writing complex JavaScript applications*.

You will be shown how to use an online IDE called **Cloud 9**, however you are encouraged to make use of any other platforms and tools.

# 1 Getting Started

## 1.1 Creating a Cloud9 Workspace

Start by creating yourself an account on **Cloud 9** (https://c9.io) and logging in. Create a new workspace by clicking on the *create a new workspace* button. Give it the name **covuni** and the  description *Full-Stack Development*. Choose the **private** option and the default **custom** template.

Now click on the **Create Workspace** button. This will create a new project.

Take a moment to configure your Cloud 9 editor. Open the preferences screen from the **Cloud 9 > Preferences** menu.

1. in the **Code Editor** section
  - uncheck the _soft tabs_ box and set the tab size to 2.
  - switch off **Autodetect tab size on load**.
  - switch on **On save strip whitespace**
2. in the **Hints and Warnings** section
  - switch off **Mark missing optional semicolons**
  - make sure **customise javascript warnings with .eshintrc** is switched on

Locate the _Terminal_ window at the bottom of the screen. We will use this to work with the _Git_ version control system. Start by cloning the lab materials:
```
git clone https://github.com/covcom/305CDE.git
```
This will clone the remote repository containing the lab materials into a directory called `305CDE/`, you should be able to see this in the workspace filetree. To run Git commands we need to be in the new `305CDE/` directory.
```
cd 305CDE/
git status
```
This command prints a status message from the Git repository.

## 1.2 Creating a New Repository

At the moment we are working on a copy of the repository hosted on GitHub. As we complete the lab activities it is important to keep a backup copy of our files. This can't be backed up on the GitHub repository since it is read-only. The solution is to create our own remote repository (on GitLab) and push the changes to this.

Create an account and log into **GitLab** (https://gitlab.com). Create yourself a new empty repository by clicking on the green **New project** button in the top-right corner of the page. In the *project path* you should enter **305CDE** and in the *Description* field enter *Developing the Modern Web 2*. Set the *visibility level* to **Private** and click on **Create Project*. You will be taken to the project home screen.

Next you need to copy the repository URL to your clipboard. It should be similar to:

`git@gitlab.com:username/305CDE.git`

Now return to the Cloud 9 Workspace. We need to update the remote repository URL so it points to our new repository. First lets check the current remote settings.
```
git remote -v
origin  https://github.com/covcom/305CDE.git (fetch)
origin  https://github.com/covcom/305CDE.git (push)
```
As you can see your workspace points to the readonly version on GitHub. Lets change this to point to our read-write repository on GitLab. Make sure you substitute your own URL.
```
git remote set-url origin git@gitlab.com:username/305CDE.git
git remote -v
origin  git@gitlab.com:username/305CDE.git (fetch)
origin  git@gitlab.com:username/305CDE.git (push)
```
You will notice that your remote called *origin* now points to your new GitLab repository.

Finally we need to configure Git on Cloud 9 with our name and email address. Make sure this matches the name and email you used when setting up your GitLab account.
```
git config --global user.name 'Your Name'
git config --global user.email 'your@email.com'
```

## 1.2 Configuring SSH Keys

We need to store our Cloud 9 public key on the GitLab server before we can securely push our changes. Locate the browser tab displaying your Cloud 9 home screen and click on the **settings** button (the small gear in the top-right of the screen). Click on the **SSH Keys** tab located down the left-side of the screen to display your public key. Select the entire key by double/triple clicking it and copy to the clipboard.

Now open your GitLab home screen and click on the **Profile Settings* button (the gear in the top-right corner of the page). Click on the **SSH Keys** tab located down the left-edge of the screen and click on the green **Add SSH Key** button. Paste the key into the large field and give it the title **Cloud 9**. Finally click on the **Add Key** button.

## 1.3 Pushing to the New Remote

The final step is to push the local copy of your repository to the new *origin* remote. This will upload all the files and change history to your own remote on GitLab.
```
git push origin master
```
If you now open the *GitLab* repository you will see a **files** link down the left-hand side of the screen. If you click on this you will see all the project files on your GitLab repository.

## 1.4 Pulling Changes

Over the course of the module there will be changes made to the original read-only repository on GitHub. To allow access to these changes you will need to add a second remote to your local Cloud 9 repository (we will label this as the *upstream* repository).
```
git remote -v
git remote add upstream https://github.com/covcom/305CDE.git
git remote -v
```
Before you start each worksheet take a few moments to sync your fork which will keep it up to date with the original.
```
git pull upstream master
```
This will pull down any new files or changes from the GitHub repository and merge them into your local copy. In this way you will always have the latest versions of the teaching materials.

## 1.5 Commiting Working Code

At the end of each exercise you should get into the habit of committing your working code.
```
git status
git add .
git commit -m 'finished exercise xxxx'
```

## 1.6 Pushing to Your Remote

At the end of your programming session you should push all these new commits back to your GitLab repository.
```
git log origin/master..HEAD
git push origin --all
git log origin/master..HEAD
```

## 1.7 Updating the Cloud Server

Finally, before starting the labs you should ensure that any unnecessary packages are removed on your cloud server. This is running **Ubuntu** and so we can use the built-in _package manager_ (apt) for this. Cloud 9 comes with several languages pre-installed (PHP, Python and Java). Lets search for any packages linked to these three languages.
```
dpkg --get-selections | grep php
dpkg --get-selections | grep python
pkg --get-selections | grep jre
```
We should now remove the software we _don't_ need. This will both increase the space available on the disk and also increase the server performance. _Autoremove_ removes any packages no longer required and cleans up the server.
```
sudo apt-get remove php5 python3 openjdk-7-jre
sudo apt-get autoremove
```
Next we need to install the _Kerberos_ dev libraries. These will be needed for our server-side scripts to communicate with various databases.
```
sudo apt-get update
sudo apt-get install -y libkrb5-dev
```

## 1.7 Next Steps

Now you are ready to start learning. Open the directory containing the first topic and follow the instructions given.

## Presentation

This is the presentation for the API completion week.

https://goo.gl/ig5Ak5