# FedoraNodeJS Project
Setting up a Dev environment in Fedora to develop in NodeJs. These are my notes to getthing that environment configured.  
[NodeJS](Documentation/NodeJS.md)
## Installing git and Configure SSH with GitHub
~~~
sudo dnf install git -y
git --version
git config --global user.name "User Name"
git config --global user.email "mymail@gmail.com"
~~~
To confirm everything is configured properly:
~~~
git config --list
~~~
Now, set up the SSH key and add it to GitHub
~~~
ssh-keygen -t ed25519 -C "myemail@gmail.com"
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519
cat ~/.ssh/id_ed25519.pub
~~~
You will need the public key, copy it. Browse to https://github.com/settings/keys and click on **New SSH Key**.
Test you key:
~~~
ssh -T git@github.com
~~~
## New Projects Originating on GitHub or Existing Projects already on GitHub
Create any new project on GitHub, then clone the repository, just as you would with an existing project you want to work on that is already in GitHub.  
* Go to the repository you want to clone.
* Find and click the **Code** button, copy the SSH link.
```
git clone <ssh link copied>
```
## Existing Code Locally, Want to Create Project in GitHub
You have existing code locally that you want to push to a new GitHub repository. This is when you create a great app then want to build on it in GitHub.
* Go to GitHub, create a New Repository
* Fill in the Repository Name
* **DO NOT** check 'Initialize with README' (leave it empty)
* Create the Repository
* Find and click the **Code** button, copy the SSH link.
* If you have files you **don't want in GitHub (like node_modules or secrets)**, create a .gitignore before commutting, see below for an example of one for NodeJS.
```
node_modules/
.env
.DS_Store
```
Go to your project folder and add the files for an initial commit, then add GitHub repository as a remote then finally push your code.
~~~
cd Documents/Repo/yourProject
git init
git add .
git commit -m "Initial commit"
git remote add origin <paste SSH link>
git branch -M main
git push -u origin main
~~~
Check to make sure the files are now on GitHub.
