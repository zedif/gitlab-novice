---
site: sandpaper::sandpaper_site
---

[GitLab] is a web application for managing [Git] repositories. Since it is build
around Git, it is suitable to manage any project that mostly works with plain
text files, for example software source code or TeX based documents. With its
built-in issue and wiki systems, it can, in certain cases, even be the right
tool for managing a project without any files.

This lesson will give you a foundational understanding of GitLab’s features, so
that you can make informed decisions on how to use it as a tool.

Since GitLab interprets many of its text fields’ values as Markdown, more
specifically [GitLab flavored Markdown][GitLabMarkdown], this lesson contains
a rudimentary introduction to Markdown syntax, following the [CommonMark
specification][CommonMark] on which the GitLab flavor is based.

[CommonMark]: https://spec.commonmark.org/current/
[Git]: https://git-scm.com/
[GitLab]: https://about.gitlab.com/
[GitLabMarkdown]: https://docs.gitlab.com/ee/user/markdown.html

# Required Previous Knowledge

GitLab is mainly a platform for Git repositories. So a major part of this lesson
requires a basic familiarity with Git. To understand the material on GitLab’s
continuous integration (CI) feature you need to know your way around the shell
and it might help to have the most basic understanding of how to use [Docker].
Knowledge on how to create and edit text files is also assumed.

[Docker]: https://www.docker.com/
