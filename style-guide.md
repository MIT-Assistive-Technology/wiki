# Coding + Collaboration Style Guide

Heavily inspired by [MIT AT GitHub + Intro Software Dev Training](https://docs.google.com/document/d/1xpCx8eqMVICehUoUG5245Ij-hrEVwxwWfV-j-afTQH8/edit?usp=sharing) and [Git + GitHub Best Practices for Teams (Opinionated)](https://dev.to/bholmesdev/git-github-best-practices-for-teams-opinionated-28h7). Would **highly** recommend reading through both!

## 1. Create an Issue
Create an issue with the following information:  
1. **Description:** if the issue is a feature, a description of the feature being added to the project; if the issue is a bug, what the bug is and how to replicate it  
1. **List of action items:** a checklist of bite-sized tasks to complete in order to complete/resolve the issue 
1. **General notes:** improvements that may be needed down the road, discussion points if the team still needs to decide on certain details

TIP: Issues can be "resolved" (completed) by a PR submission via [keywords](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/using-keywords-in-issues-and-pull-requests). This will help with project management!

## 2. USE BRANCHES
ALWAYS create a new branch to implement the issue (or really, any code that you want to contribute):  

`git checkout -b branch name-of-your-branch`

Branch naming guidelines:
1. Start the branch name with either your name or your Git(hub, lab, whatever) username. In the example: 'xqiuu'
1. Include the issue number your branch resolves. In the example: '25'
1. Add a 4-5 word title on what your branch does, separating the words with dashes. In the example: 'add-software-style-guide'
Example: xqiuu.25.add-software-style-guide

**Merge main back into your branch often** to have the most up-to-date code:

```
# 1. Temporarily shelve any uncommitted changes
git stash

# 2. Get the latest version of main from GitHub
git fetch origin

# 3. Merge the latest main into your current branch
git merge origin/main

# 4. Restore your uncommitted changes
git stash pop
```

Think of this as “syncing” to the ground truth, and it will help you avoid merge conflicts when you’re finally ready to merge BACK into main.

## 3. Make Changes
Follow these guidelines for clear code:

**Naming:**
Names of variables, functions, and classes should be short, intuitive, and descriptive.

- Good examples: user_id, get_user(), DatabaseClient, is_valid_input
- Bad examples: x, thing, temp2, doStuff(), MyClass

_NOTE:_ avoid abbreviations as much as possible. In the example above, 'id' is okay, but anything more obscure just makes reading code more difficult.

**Functions:** Keep them short and single-purpose. Create new functions for repetitive code (Don't Repeat Yourself, or DRY).

Use docstrings above each function to explain the following:  
1. Summary: explain what the function does  
1. Arguments / Parameters: A list of all input variables, their expected data types, and what they do.  
1. Return Values: The data type and meaning of the output returned by the function.  
1. Raises / Exceptions: A breakdown of any errors the function intentionally raises and why.
2. Assumptions: If the function requires certain behavior before or after the function is invoked, make it extremely clear in the docstring. Learn more from [6.102 notes](https://web.mit.edu/6.031/www/fa21/classes/06-specifications/).
1. (Optional) Examples: code snippets showing how to invoke the function and its expected output.  

You can find more information on docstrings for Python on [this website](https://peps.python.org/pep-0257/#multi-line-docstrings), and use the VSCode Extension "autoDocstring - Python Docstring Generator".

_NOTE:_ the only exception to the DRY rule is when it comes to test cases. Sometimes, for the sake of readibility of test cases, it's okay to repeat code IFF it clarifies the behavior of the test case. Make your best judgment.

**Comments:** Keep comments concise and updated. Delete ones that are no longer relevant.  
Use TODO comments for things that need to be fixed or haven’t been done yet.
- Abide by the following format: 'TODO (#XX): DESCRIPTION' where XX is the associated issue (this implies you MUST file an issue!)
- If you write a TODO in VSCode: with the write extensions for your-favorite-coding-language, the color of the TODO message should be different.
- You can also easily cmd + f for all instances of it :)

**File organization:** 
One component/class per file where reasonable.
- Group by feature, not by file type, unless the project already follows a different convention.  
- Files should be SHORT. Use import statements to bring functions from one file into any other files.
- Highly recommend whiteboarding out any project before tackling it.

_NOTE:_ AI has a tendency to create new files when it really doesn't need to. Sometimes the best thing you can do is understand your code base well yourself, and direct your-favorite-AI-agent to do your bidding--exactly where you want it to.

### Language Style Guides:
[python](https://peps.python.org/pep-0008/)
[JavaScript](https://github.com/airbnb/javascript)
[C++ (Google's Style Guide)](https://google.github.io/styleguide/cppguide.html)
(may add more)

## 4. Commit Changes
**Main should ALWAYS compile and run successfully**.

Don't commit directly to main. Do the following instead:
1. Create or identify an Issue.
1. Assign the Issue to yourself (so others know not to tackle it at the same time).
1. Create a branch.
1. Commit your changes to the branch.
1. Merge main INTO your branch to resolve conflicts.
1. Open a PR for your branch. Make sure to use [keywords](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/using-keywords-in-issues-and-pull-requests) to link the PR to the corresponding issue.
1. Get your PR reviewed by a teammate.
1. Once approved, use the PR to merge into Main.

Commit small, commit often! A note on commit messages, too:
- Don’t lose your work.
- Don’t do such large commits such that if something breaks, you will be able to revert easily and not have to redo a ton of work.  
- Write commit messages as short, 50-character-or-less phrases describing the action taken in the **imperative tense**: ``` git commit -m "fix profile picture" ```

## 5. Testing
Create test files to test function/class assumptions. 

For Python: we recommend looking into [Pytest] (https://docs.pytest.org/en/stable/getting-started.html).
- These are unit tests for testing specific functions and their behaviors.
- We also recommend doing “integration tests” before merging, which is to make sure the entire system still runs together, not just the parts you changed.
- All tests should be run using CI/CD for each project's repository.


## 6. Pull Requests
Before merging a branch into main (but after doing your own unit tests), create a pull request and get someone on your team to sign off on your code changes before it merges!

This helps with “tech debt” → other members of your team can learn about your code, help debug, and maintain it if you are no longer on the team.

PR description should include:  
1. What changed and why.
1. How to test it.
1. Linked issue using keywords (i.e.: Closes #123)
1. Ensure CI passes (tests, build) before requesting review.

Reviews:
- Respond to review comments with either a fix or a brief explanation.
- **As a reviewer:** approve if it's good enough. Nitpicks go in a comment marked 'nit:' and should NOT block merging.
- Once peer reviewed, choose one of the merge methods (i.e. confirm merge, squash and merge) to perform the merge.
- Delete the feature branch.
