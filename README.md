# Git Workflow Simulation
For managing product releases that need to happen on the 25th of every month, a structured Git Workflow can help maintain a smooth development, testing, and release process. Below is a Git Workflow Architecture that you can implement:

# Git Workflow Architecture:
**Main Branch** (Production)
This branch should always be stable and contain code that has been tested and is ready for production.
The product release on the 25th of every month will be made from this branch.

**Develop Branch**
The branch where the integration of new features and bug fixes happens.
Regular updates are merged into the develop branch from feature branches.
It serves as a base for testing and QA.

**Feature Branches**
Each new feature or bug fix gets its own branch, created off the develop branch.
Once completed and tested locally, they are merged back into the develop branch.

**Release Branches**
Before the 25th of the month, a release branch is created from develop. This branch will be used for final testing, bug fixing, and preparing for deployment.
No new features should be added to this branch, only fixes and final preparations for the release.

**Hotfix Branches**
For emergency bug fixes that need to be applied directly to the main branch. After applying a fix, it should also be merged back into develop and the relevant release branch (if it exists).

**Version Tags**
Each release on the 25th should be tagged with a version number (e.g., v1.0.0) for easy reference and rollback if needed.

# Example Workflow:

Developers work on feature/xyz branches.
Completed features are merged into the develop branch.
On the 15th of the month, create a release branch (release/v1.x.x) from develop.
Perform final testing, bug fixes, and documentation updates on the release branch.
On the 25th, merge the release branch into main and create a tag (v1.x.x).
Deploy the code from the main branch to production.

# Pseudo Code and Simulation:
To simulate this workflow, you can create the following Git branches and commit some pseudo code files to represent changes.

**Branch Creation:**
Create a main branch.
Create a develop branch off main.
Create feature branches (feature/feature1, feature/feature2).
Create a release branch (release/v1.0.0).

**Pseudo Code:**
Commit simple text files representing code for features (e.g., feature1.txt, feature2.txt).

**Merging:**
Merge feature branches into the develop branch.
Merge the release/v1.0.0 branch into main on the 25th



# GIT CODE

**Initialize the repository and set up the main branch:**
mkdir git-workflow-simulation
cd git-workflow-simulation
git init
echo "# Git Workflow Simulation" > README.md
git add README.md
git commit -m "Initial commit on main branch"
git branch -M main
git remote add origin https://github.com/MukulChauhann/new_repo.git
git push -u origin main

**Create and switch to the develop branch**
git checkout -b develop
echo "This is feature1" > feature1.txt
echo "This is feature2" > feature2.txt
git add feature1.txt feature2.txt
git commit -m "Add initial feature files on develop branch"
git push -u origin develop

**Create feature branches (feature/feature1, feature/feature2)**
*For Feature 1*
git checkout -b feature/feature1
echo "Feature 1 development" > feature1.txt
git add feature1.txt
git commit -m "Develop feature1"
git push -u origin feature/feature1

*For Feature 2*
git checkout develop
git checkout -b feature/feature2
echo "Feature 2 development" > feature2.txt
git add feature2.txt
git commit -m "Develop feature2"
git push -u origin feature/feature2

**Merge feature branches back into develop**
*Merging feature1 into develop*
git checkout develop
git merge feature/feature1
git push origin develop

*Merging feature2 into develop*
git merge feature/feature2
git push origin develop

**Create a release branch from develop**
git checkout develop
git checkout -b release/v1.0.0
echo "Release notes for version 1.0.0" > release_notes.txt
git add release_notes.txt
git commit -m "Prepare release v1.0.0"
git push -u origin release/v1.0.0

**Merge the release branch into main for the final release on the 25th**
git checkout main
git merge release/v1.0.0
git tag v1.0.0
git push origin main --tags

**Delete the feature and release branches after merging (optional)**
git branch -d feature/feature1
git branch -d feature/feature2
git branch -d release/v1.0.0
git push origin --delete feature/feature1
git push origin --delete feature/feature2
git push origin --delete release/v1.0.0



