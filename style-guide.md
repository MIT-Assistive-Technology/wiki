# Project Repo Style Guide

Heavily inspired by https://docs.google.com/document/d/1xpCx8eqMVICehUoUG5245Ij-hrEVwxwWfV-j-afTQH8/edit?usp=sharing and https://dev.to/bholmesdev/git-github-best-practices-for-teams-opinionated-28h7

## 1. Create an Issue
Create an issue with the following information:  
**1. Description:** if the issue is a feature, a description of the feature being added to the project; if the issue is a bug, what the bug is and how to replicate it  
**2. List of action items:** a checklist of bite-sized tasks to complete in order to complete/resolve the issue  
**3. General notes:** improvements that may be needed down the road, discussion points if the team still needs to decide on certain details

## 2. USE BRANCHES
Create a new branch to implement the issue:  

`git checkout -b branch name-of-your-branch`

Branch naming guidelines:
1. Start the branch name with either your name or your Git(hub, lab, whatever) username.  
2. Include the issue number your branch resolves.
3. Add a 4-5 word title on what your branch does, separating the words with dashes. 
Example: xqiuu.25.add-software-style-guide

Merge main back into your branch often to have the most updated code:

```
# 1. Temporarily shelf your uncommitted changes
git stash

# 2. Pull the latest code from main
git pull origin main

# 3. Restore your shelved changes back onto your working space
git stash pop
```

Think of this as “syncing” to the ground truth, and will help you avoid merge conflicts when you’re finally ready to merge BACK into main.

## 3. Make Changes
Some tips for writing clear code:

**Naming:**
Names of variables, functions, and classes should be short, intuitive, and descriptive.  

**Functions:** Keep them short and single-purpose. Create new functions for repetitive code (Don't Repeat Yourself).

Use docstrings above each function to explain the following:  
1. Summary: explain what the function does  
2. Arguments / Parameters: A list of all input variables, their expected data types, and what they do.  
3. Return Values: The data type and meaning of the output returned by the function.  
4. Raises / Exceptions: A breakdown of any errors the function intentionally raises and why.  
5. (Optional) Examples: code snippets showing how to invoke the function and its expected output.  
You can find more information on docstrings for Python on [this website](https://peps.python.org/pep-0257/#multi-line-docstrings), and use the VSCode Extension "autoDocstring - Python Docstring Generator"

**Comments:** Keep comments concise and updated. Delete ones that are no longer relevant.  
Use TODO comments for things that need to be fixed or haven’t been done yet. If you write TODO in VSCode, and have the Python extensions installed, the color of the TODO message should be different. You can also easily cmd + f for all instances of it.

**File organization:** 
One component/class per file where reasonable; group by feature, not by file type, unless the project already follows a different convention.  
Files should be SHORT. Use import statements to bring functions from one file into any other files.
### Language Style Guides:
[python](https://peps.python.org/pep-0008/)
[JavaScript](https://github.com/airbnb/javascript)
(may add more)

## 4. Commit Changes
Main should ALWAYS compile and run successfully. It should not be committed to directly; instead, you should commit your changes to the branch you created for the issue.
Commit small, commit often --
Don’t lose your work. Don’t do such large commits such that if something breaks, you will be able to revert easily and not have to redo a ton of work.  
Write commit messages as short, 50-character-or-less phrases describing an the action taken in the imperative mood:
``` git commit -m "fix profile picture" ```

## 5. Testing
Create test files to test those assumptions.  
I would recommend looking into [Pytest] (https://docs.pytest.org/en/stable/getting-started.html).
These are unit tests for testing specific functions and their behaviors
I would also recommend doing an “integration test” before merging, which is to make sure the entire system still runs together, not just the parts you changed.


## 6. Pull Requests
Before merging a branch into main (but after doing your own unit tests), create a pull request and get someone on your team to sign off on your code changes before it merges! This helps with “tech debt” → other members of your team can learn about your code, help debug, and maintain it if you are no longer on the team.

PR description should include:  
1. What changed and why  
2. How to test it 
3. Linked issue (Closes #123)
4. Ensure CI passes (tests, build) before requesting review.
Respond to review comments with either a fix or a brief explanation.

As a reviewer: approve if it's good enough Nitpicks go in a comment marked nit: and shouldn't block merging.

Once peer reviewed, choose one of the merge methods (i.e. confirm merge, squash and merge) to perform the merge.

Delete the feature branch.