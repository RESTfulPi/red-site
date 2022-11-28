---
layout: default
parent: Development
nav_order: 9
---

# Website

## Overview

The project website is open source, which furthers the idea of allowing future teams to build off of existing code. The repository with all of the source code for the website can be accessed [here](https://github.com/4850-red/red-site). To streamline the web development process, the static site generator Jekyll was used along with Github Pages to automatically deploy the changes.

## Jekyll

[Jekyll](https://jekyllrb.com/) takes plain text and converts it into a full website.
[Just the Docs](https://just-the-docs.github.io/just-the-docs/) is a theme for Jekyll
that makes creating online documentation easy. Jekyll also has support for
[Github Pages](https://pages.github.com/), so a site can be built and deployed after
commits to a Github repository.

### Source code

```markdown
[Jekyll](https://jekyllrb.com/) takes plain text and converts it into a full website.
[Just the Docs](https://just-the-docs.github.io/just-the-docs/) is a theme for Jekyll
that makes creating online documentation easy. Jekyll also has support for
[Github Pages](https://pages.github.com/), so a site can be built and deployed after
commits to a Github repository.
```

## Github Pages

Github Pages is a service provided by Github that hosts a website directly from a Github repository. This has several advantages. First, teams do not have to pay for a server or self host one, and they do not have to pay for a domain. Second, Github Pages utilizes version control, which allows for concurrent development between users and keeps a full history of all changes made in the repository. Pages can be expanded upon further with third party tools and [Github Actions](github-actions).
