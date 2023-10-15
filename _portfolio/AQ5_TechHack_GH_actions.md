---
title: "Tech hack experiment: check file changes in a repo using Github Actions"
---

A tech hack experiment - using Github Actions to automate the checking of repos for file changes.

A technical writer might want to constantly be checking which files in a repo have been updated. These files may be either in Markdown or code,

- You can view the [test repo](https://github.com/bennetthub500/github-demos) here.  

- View the [log](https://bennetthub500.github.io/personal/pdfs/TechHackScreenshot_GH_Actions.png) of one workflow test run by me, where I altered a file named Test file 1.txt in this test repo.   

Another way of automating this task could involve writing a shell script.  I learned recently that Github Actions is increasingly popular and easy to implement, so I wanted an excuse to explore it.  

The Github Action I used was pre-written. You can use many off the shelf actions, and contribute your own.  

Another use case for technical writers could be to implement the pre-written [Vale linter](https://github.com/marketplace/actions/vale-linter) Github action to perform style guide checks, or other custom workflows. 

