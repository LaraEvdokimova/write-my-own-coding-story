https://codingstories.io/become-author/guide

How to Write Your Coding Story

So, you’ve decided to write your own story? Great! Here’s an easy-to-follow step-by-step guide that shows you how to streamline the process.

Define a Goal
First, you need to define the goal of your story. Do you want the reader to learn something new from your story or understand an important concept? Good. Start by defining the #1 thing you want the reader to take away from your story and keep it in mind while writing.

Here are a few examples of possible story goals:
Show how to improve code readability
Provide an example of a TDD practice
Show how to implement a SOLID principle in the code
Beginner’s guide to writing a new Hello World app
Guide to legacy app refactoring

Finally, keep in mind that if the story has several goals, there's a good chance it won't reach any of them. A reader could be confused understanding what is this story about, follow one storyline and lose another. Keep it simple and targeted.

Choose a Story Name
A good story starts with a good name. It must be short and related to the functionality of software components in the story. 2-3 words are enough. Use caution when it comes to naming a story based on its goal, because many stories have similar goals.

The code inside a story usually unique, so it makes the most sense to name the story based on the purpose of the functionality inside. Here are a few examples to guide you:

Bowling Kata Story: A good name for a story about, well, bowling!
Spring Boot Starter Story: A good name for a story about getting started with Spring Boot
Garage Service Story: A good name for a story that focuses on a software package for a public garage
Balance Recalculation Story: A good name for a story that illustrates how the method for balance recalculation can be refactored to decrease complexity

Even if your story name is similar to another one, don’t worry – you will have the chance to describe how your story is different.

Create Git Repository
Each refactoring story is a branch in the Git repository, so you need to create this yourself. Create a folder with the name of your story using a notation in this format:

Story name: Garage Service Story to folder name: garage-service-story-java
The language suffix allows for easy identification of which language is used for the code inside a story and, in case the story is translated into several languages, helps users to find the necessary version.

Now, it's time to create a repository:

cd <story folder>
git init

Create Initial Code State
Your first commit is the story code in its initial form. Be sure to use well-known code organization and folder structure, so the reader doesn't have to spend time trying to understand code organization. Provide build files, so the code can be checked out and built via available tools. Remember - your story project is an example, but still a software project.

The code in the first commit must have no compilation errors and have a certain degree of completeness. Even it's an example, the reader must be able to imagine a system where this code can exist, and how components represented in the story can be used in real life. Use interfaces to define external dependencies. If the reader can see that the code is complete, it will feel more real, which will help them learn.

Don't forget to add the README.md to the first commit using the below template:

Template for README.md
See an example of README.md:

Readme file
Create Final Code State
Now, feel free to implement the story goal without recording and explaining every step. Create a final state at your own pace and work through the approach making any required commits. You need to think about how the story goal will be reached, find potential flaws in the initial task and think about the story’s future steps. Maybe while working on the final state, you will find that the initial task must be reworked.

Plan Step-by-Step Changes
Now, look at the final code, remember what you did to get it to that state, and create a plan of step- by-step changes. Do not make changes and record commits – just jot down a quick plan like this:

Change class name to this one because it violates [x]
Introduce new method and move some code inside to decompose logic
Rename variable and delete obsolete comments to make code clean
…
Remove unnecessary method because we didn’t need it anymore
Try to make every change small, and do not make mix several different steps into one. It's better to change a small amount of code in each step so as not to overwhelm the reader.

Record the Story
Now it's time to record the story. Remember, every page is a commit, so you are going to make commits. Every commit has page text in the .story.md file and, optionally, some code changes. The code changes are optional because some pages may only have explanatory text.

Project's folders
There could different types of pages in the story, but for now, here are some best practices:

You can use markdown for the page's text about tweaks. Read more here.
Use links to help the reader follow your explanations. They will help to load specific files and stay in line in the File View. Read more about links.
Use autofocus to open a file as soon as the page is loaded. It will help users to see the context of the page more clearly. Read more about autofocus.
Put a page header in the commit message for page’s commits. It will help you to find the needed page using the Git log command later.
If there's a code change, ensure code can be compiled and is green if it has unit tests or red if it’s an exception. Otherwise, the reader will start to think that incomplete changes are a good practice.

First Page
It's good to use the first page to introduce and explain the story’s goal. The same text will be added to README.md if the story is opened as a Git repository in GitLab. Present classes or other components of the code base and explain their roles and responsibilities or your assumptions about their roles and responsibilities. Use the story name as a header for the first page so the user will be sure they opened the right story. Set up an autofocus to show the most important component as soon as the story is opened. Inspire the reader to review the code structure by themselves.

Example of the first page
Investigation Page
Think of this part of your story as an investigation where you record some kind of refactoring of "unknown code," thus you need to not only change the code, but to understand it as well. The investigation page helps you to review a small part of the code base, ask questions about its current state, identify problems and provide reasons why the problem is a problem. It's a good practice not to show code changes on the page, so the reader doesn't see a solution before the analysis of a problem is complete.

Example of investigation page
Refactoring page
As soon as the investigation is complete and the problem is identified, it's time to make code changes. The page text in .story.md must contain an explanation of the changes made and, if necessary, clarify why the changes you make are better than alternatives.

If changes are small and obvious, then it may be possible to combine the investigation and refactoring pages.
Example of refactoring page
Last Page
The last page must be used to summarize changes made, remind the reader of the story goal, and motivate the reader to review the solution once again. If there are more potential improvements to be done by the reader as an optional assignment, then be sure to explain the next steps.

Example of the last page
Rewriting the Story
It's absolutely fine if you need to rewrite some pages of your story if you find a typo, decide to reword a sentence, fix broken links, etc. As soon as the story is a git history, you need to rewrite this history using git rebase. There are two types of changes you can make – either to the page text or to the page code. We do not recommend mixing both types of changes due to the specifics of rebase and the difficulties of merging a .story.md file with the default merge strategy.

Rewriting the Page's Text
Do not use the tag old_page in your repository. It will be rewritten by the command below.
Do not use this method if you have anything other than page text changes. It won't work because only the .story.md file will be added to the staging area.
If you need to change only the text content of the page, you can use git rebase with a specific merge strategy - theirs. This would help to avoid merging the .story.md file conflict on every page. It will be necessary as soon as you use the same file to completely change its content in every commit, keeping in mind that the git default merge strategy doesn't handle it well.

Install additional git command by executing in the console (once per laptop):

git config --global alias.rewrite-page-text '!git tag -f old_page && git
add .story.md && git commit --amend --no-edit && git rebase -s recursive -
Xtheirs old_page master --onto HEAD && git tag -d old_page'
Checkout the commit of the page with the text you want to change:

git checkout <page>
Make changes to the text and use the command rewrite-page-text to save changes and rewrite the story:

git rewrite-page-text
Don't forget to push story changes to the remote repository if you already published it:

# You need to make master branch unprotected to allow force push
git push -f
If you prefer to have manual control of page and story rewriting, the next commands are needed:

Rewriting the Page's Code
If you need to rewrite code, you need to use the usual rebase with default merge strategy to ensure changes to earlier pages exist in later pages. Do not use the method above for page text or you will make code changes in only the current page code. You will need to fix all merge conflicts on your way. Read more about rebase if necessary.

Feel free to use your preferred way to rewrite history, like if you want to use interactive rebase because you need to remove or split pages.
# Keep reference on old page commit
git tag -f old_page
# Add .story.md changes to staging
git add -A
# Rewrite page commit (--no-edit is not changes to commit message are needed)
git commit --amend --no-edit
# Rebase all commits above on the top of new commit and merge conflict
git rebase -s recursive old_page master --onto HEAD
# Remove temporary tag from old page commit
git tag -d old_page
Publishing the Story
As soon as the story is ready, you need to prepare it for publishing.

Tag Initial Commit
First, tag task on the initial commit. It will help the reader to checkout tag if they decide to solve the task by themselves or to repeat changes you explain in the story.

# Checkout initial commit
git checkout <initial commit>
# Task initial commit to checkout it easily
git tag task
# Return back to master
git checkout master
Create Repository in git.epam.com
Now you need to create the repository in the Refactoring Stories group of git.epam.com: https://git.epam.com/Refactoring-Stories

Name convention for repository is <name of the story>-story-<language>. Use a hyphen instead of spaces in the story name.

For example, if the story name is Garage Service Story, then the repository must be named garage-service-story-java.

Choose “internal” visibility if you want your story to be read by other developers.
Git visibility repository
Push Your Story
Use instructions provided by GitLab to push a story's repository.

Git commands
Unprotect Master Branch
By default, GitLab protects the master branch from force pushes, which is something you need to do a lot of while working on the story. To allow forced pushes, unprotect master branch in the Settings -> Repository page of the story repository:

Git protect a branch
Open Story in the Coding Stories UI
Open http://rs.delivery.epam.com and enter the full URL into the repository in GitLab. Do not use the link to clone the repository - just link to open it in the UI.

Git protect a branch
Story Syntax Guide
Live Example
Read our Hello World Story for a live example of story page syntax and UI capabilities: https://epa.ms/hello-world-story

Markdown
Markdown with additional commands must be used for story text. Here’s a general reference to supported markdown: https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet

Links
You can add page text links to the file in the project tree. Just use regular markdown links with a relative path to the file:

... [text of link](<path>/<to>/<file>/<from>/<the>/<root>/<folder>) ...
You could also provide specific line numbers or a range of lines in the link. The UI will open the file, scroll to specific lines if necessary, and highlight them:

# Scroll and hightlight specific line
[text of link](<path>/<to>/<file>/<from>/<the>/<root>/<folder>:<line number>) ...

# Scroll and hightlight range of lines
[text of link](<path>/<to>/<file>/<from>/<the>/<root>/<folder>:<line number from>-<line number to>) ...
If the file was changed on this page, a link with line numbers will point to and highlight lines in a new version of the file. If you want to make a link to a line in the previous version of the file, you could add the keyword old to the end of link:

# Scroll and hightlight specific line in previous (old) version of file
[text of link](<path>/<to>/<file>/<from>/<the>/<root>/<folder>:<line number>:old)

# Scroll and hightlight range of lines in previous (old) version of file
[text of link](<path>/<to>/<file>/<from>/<the>/<root>/<folder>:<line number from>-<line number to>:old)
For example, if the folder src is in the root of the story's repository:

# Link to open file
Let's take a look on the [method](src/main/java/com/epam/engx/story/GarageService.java)

#Link to open specific file, scroll to line and highlight it
Let's take a look on the [method](src/main/java/com/epam/engx/story/GarageService.java:15)

#Link to open specific file, scroll to first line in range and highlight whole range
Let's take a look on the [method](src/main/java/com/epam/engx/story/GarageService.java:15-19)

#Link to open specific file, scroll to line in previous verion of file and highlight it
Let's take a look on the [method](src/main/java/com/epam/engx/story/GarageService.java:15)

#Link to open specific file, scroll to first line in range in previous verion of file and highlight whole range
Let's take a look on the [method](src/main/java/com/epam/engx/story/GarageService.java:15-19:old)
Autofocus
If you want a certain file and line to be shown in the file view as soon as the reader opens the page, please use the special command focus surrounded with '---' on the top of page text:

---
focus: <path>/<to>/<file>/<from>/<the>/<root>/<folder>:[optional line number]
---
### Header
Story text
Video
You can add embedded video directly to the story page text. Below is an example for https://videoportal.epam.com.

Get Code of Embedded Video
Get Code of Embedded Video
Add It to the Page Text in .story.md
Add It to the Page Text
Watch It on the Story Page
Watch It on the Story Page
Quiz
It's possible to add a simple quiz to your story page to verify that readers have learned the material. Only one-line answers are supported at this stage.

When a quiz question is not answered correctly, the reader won't be able to open the next page. Try to go easy on the reader so they don’t get frustrated or stuck. Ask questions about only high-level points of your story – don’t try to trick them.

Have Questions about Becoming an Author?
We’re here to help! Drop us a line and we’ll get back to you right away.
AskEngX@epam.com

Contact us:  AskEngX@epam.com

About
Stories
Become an Author

© 2020 EPAM Systems, Inc. All Rights Reserved.
Powered by 
