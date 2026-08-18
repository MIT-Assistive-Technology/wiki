# Open Source Style Guide

As a club aiming to create... well Assistive Technology, we should ALWAYS aim to **open source our projects**.

Why? A project should ideally be useful beyond the one semester or team that built it. Open sourcing makes it easier for:

* Future AT teams to continue/maintain the project instead of starting from scratch.
* Disabled people with similar needs may use or adapt what we built.
* Other students, researchers, and organizations can potentially improve the project.
* Co-designers can use and modify their technology, even after the team alums from the club.

**The goal is NOT just to put code on GitHub.** The goal is to leave behind something that another person could _realistically_ understand, build, and use themselves.

## 1. Make the Repository Public

Once your co-designer and team are comfortable sharing the project, make the GitHub repository **public**.

**Before making anything public:**

* Remove API keys, passwords, tokens, private URLs, and other secrets.
* Remove personal information about your co-designer unless they have explicitly agreed to share it.
* Make sure any datasets, images, libraries, CAD files, etc. are allowed to be redistributed.

*NOTE:* Open source does NOT mean everything has to be public. Protecting co-designer and team member privacy comes first.

## 2. Write a README

Every open-source project should have a `README.md` that explains enough for someone outside your team to understand the project.

At minimum, include:

1. **What is this?** A short description of the project and the problem it solves.
2. **How does it work?** A high-level overview of the system + architecture.
3. **How do I set it up?** Clear installation + build instructions.
4. **How do I use it?** Basic usage instructions.
5. **What do I need?** Required hardware, software, dependencies, etc. Cost would also be nice, and any BOMs!
6. **Current limitations:** What doesn't work yet? What assumptions does the project make?

**TIP:** Pretend you disappeared tomorrow. Could another MIT AT member clone the repository and figure out how to recreate or run the project?

## 3. Make Setup Reproducible

Someone should NOT have to message the original team asking "what version of this library did you use?"

Where possible:

* Include dependency files (`requirements.txt`, `package.json`, etc.).
* Document required software versions.
* Include setup scripts or build instructions.
* Document required hardware and where to get it (this is where the BOM is very very nice to have).
* Include CAD, PCB, firmware, or other design files needed to reproduce the project.

**Test your instructions on a fresh machine/environment if possible!**

And most of all, keep this all organized well within the project. Imagine getting thrown like 1000 files... but now knowing where to start! This is why the README file is so powerful.

## 4. Add a License

Add an open-source license so people actually know what they are allowed to do with your work.
- Without a license, code being publicly visible on GitHub does **not** automatically mean other people are allowed to reuse or modify it.
- For most projects, use the license agreed upon by exec and add it as a `LICENSE` file in the repository. TODO (alisonsoong): We have not yet set a standard, but we will soon!!
- **If your project incorporates other open-source software, make sure you follow their license requirements too.**

## 5. Leave the Project Maintainable

Before wrapping up each semester (not even at the end of the project!!! EVERY SEMESTER PLEASE):

* Resolve or document major bugs.
* Create Issues for unfinished work.
* Delete abandoned code/files that are no longer relevant.
* Make sure `main` works (should be covered by CI/CD if a software project).
* Update the README to reflect the project's **current** state.
* Add documentation for anything that took your team a long time to figure out.
* Contact information for maintainers.

**For unfinished features, create Issues instead of leaving mysterious TODOs everywhere.**

## 6. Document More Than Just Code

Assistive Technology projects often include much more than software :) especially in this club where we have a lot of meche/ee projects too.

Open source whatever is useful and appropriate:

* Code
* CAD files
* Circuit diagrams / PCB files
* Bill of Materials (BOM)
* Assembly instructions
* 3D printing settings
* Hardware setup
* Design decisions
* Testing procedures

The closer someone can get to **actually reproducing the device**, the more useful the open-source project is.

## The General Rule

When your project ends, ask:

> **Could someone who has never met our team understand, reproduce, and continue this project using only what we left behind?**

If the answer is yes, you're probably in prettyyyyy good shape :)
