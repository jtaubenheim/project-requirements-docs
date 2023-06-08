---
title: Home
summary: "This proof-of-concept site leverages the Scale Computing Minimalist Documentation Template that was developed by the LSC team."
permalink: index.html
toc: true
---

[Link to the source repo for this template](https://github.lab.local/dev/docs-template-gh-pages/tree/gh-pages-minimal)

## Purpose

This site has been initially stood-up to demonstrate the features, capabilites, and usability of the in-house developed documentation solution that Scale has put forth over the past months. It utilizes a specific template that is designed to allow users to get up and running quickly with their documentation needs in a locally hosted, repo-specific, and centralized authoritative documentation source. It is designed to incorporate documentation efforts in tandem with code production by leveraging CLI and IDE interfaces that allow for rapid doc generation. 

### 1. To Edit / Create Documentation

```
git clone git@github.lab.local:dev/projreqs-docs.git

cd projreqs-docs/docs/content

nano (or your choice of editor) <filename.md>

git push
```

{% include note.html content="Make sure you include the appropriate [frontmatter](https://github.lab.local/pages/dev/docs-template-gh-pages/mydoc_getting_started.html#page-frontmatter) for newly created pages with a permalink URL or Jekyll will not render the page. You also need to make sure and include that permalink in the navigational scheme or there will not be a mechanism for users to navigate to said content (see Step #2 below:)." %}

### 2. Navigation

Users will not be able to navigate to your documentation until the navigational structure has been appropriately configured. You can organize your content and customize the hierarchical structure of your documentation so that it logically flows throughout the site based on topic, sub-topic, and level of information. Refer to the Docs Manual section on [Structure and Categorization](https://docs.google.com/document/d/1QUcu7YrE9ZX6NF1lO5vzNCrpsLqnzfFpJiJWdAmyxNY/edit#heading=h.2wqsuu3963w6) for examples on logical documentation structure.  

Change the headings, set drop-downs, and set links to other resources in your top navigation by editing the ```docs/_data/topnav.yml``` file. Refer to the full template site to learn more about customizing top navigation. 

{% include note.html content="This version of the minimalist template does not include a sidebar feature. Refer to the [Full Documentation Template](https://github.lab.local/pages/dev/docs-template-gh-pages/) to browse additional features." %}  

## Summary

An important thing to remember for all documentation you wish to have viewable on the site is that the ```permalink``` frontmatter element in each document **must** match the markdown file name and that it must end with ".html". Then plug your documentation's html addresses into your navigational scheme and you're all set. It is **strongly recommended** you refer to the information on the [Getting Started](https://github.lab.local/pages/dev/docs-template-gh-pages/mydoc_getting_started.html) page on the full template site for more detailed information about producing documentation, customizing site navigation, and things you can do with GitHub Pages. 
