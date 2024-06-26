---
title: "Tech hack experiment: check file changes in a repo using Github Actions"
---

A tech hack experiment - using Github Actions to automate the checking of repos for file changes.

A technical writer may need to constantly check a repository for changed files to perform edits. These files may be either in Markdown or code.  I learned recently that Github Actions is increasingly popular and easy to implement, so I wanted an excuse to explore it.  

I created a test repository, and utilized Github Actions to create a workflow to create the automated workflows that can be triggered in customizable ways. 

- You can view the [test repo](https://github.com/bennetthub500/github-demos) here.  

- View the [log](https://bennetthub500.github.io/personal/pdfs/TechHackScreenshot_GH_Actions.png) of one workflow test run by me, where I altered a file named Test file 1.txt in this test repo.   

Another way of automating this task could involve writing a shell script.  The Github Action I used was pre-written. You can use many off the shelf actions, and contribute your own.  

Another use case for technical writers could be to implement the pre-written [Vale linter](https://github.com/marketplace/actions/vale-linter) Github Action to perform style guide checks, or other custom workflows. 

