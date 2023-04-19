---
title: "Docs sample: Reference doc for SaltStack python module"
---

Open source configuration management product docs update

Completed a major content update to an important documentation page for SaltStack, an open source configuration management and remote execution product.   

View the [original document](https://docs.saltproject.io/en/latest/ref/states/all/salt.states.file.html#salt.states.file.comment) live
View the [edited document PDF](https://bennetthub500.github.io/personal/pdfs/SaltDocsExample1.pdf)) - edits in highlight, deletions in strikethrough

**Company context:** SaltStack, an open source application initially released in 2011 and now owned by VMWare, has a very large and fragmented set of docs utilizing a dated custom implementation of Sphinx.  As part of Salt’s long term docs plan, the revised Python module documentation page in this example is intended to serve as an example for all other Salt modules pages.  

**Process for this document:**  I joined SaltStack’s docs working group as a volunteer in late 2022.  Collaborating with a senior technical writer, I executed existing plans for improving Salt’s Python module documentation. 
I engaged SME’s on Salt’s docs Slack channels and gathered input for the Salt States file module :
- Additional use cases 
- Additional code examples
- New section headings to facilitate scanning and fit with future updated information architecture
- New resources for less-experienced users
- Copyedits to function and parameter descriptions to enhance clarity and correct the usage errors of non-pro writers

**Audience and Problems to solve:** The audiences for module docs are systems administrators and software developers. Some readers will be new to Salt and in need of a grounding in basic information, and others are experienced developers and admins who only need reference.  Style guides and documentation best practices were not followed for much of the content, despite the success of the product and adoption by major companies such as Oracle, Netsuite, and LinkedIn.  The work in this example also needed to be compatible with future Sphinx updates that will enable more TOC’s and more flexible and intuitive navigation.   

**Status:** Due to review delays, the pull request with the changes shown here has not been merged yet.  I will update this page when the PR is accepted, and later when edits are published.  In the meantime, you can view the works in progress. 
