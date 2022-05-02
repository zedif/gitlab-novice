---
title: "Merge Requests"
teaching: 0
exercises: 0
---

::: questions

- How can I contribute to a project on GitLab?

:::

::: objectives

- Fork a project.
- Create and edit a file on GitLab.
- Create/Accept a merge request.
- Mention an issue in GitLab markdown.

:::

In the chapter on collaboration we learned how to contribute changes to a
project that we are a member of. We also learned, in the previous chapter, that
we can contribute to other projects by filing issues to report problems or ask
questions. This episode we will learn about a way to suggest concrete changes to
a GitLab project that we do not have write access on.

The feature that allows us to do this is called Merge Request, the corresponding
feature on GitHub is called Pull Request. As a target for our merge request, we
will use our co-learners repository. We we have write access to it, but to learn
something new, we will pretend that we don’t.

We will create a merge request that adds a file listing the contributors, which
will solve the issue that we filed during the last episode.

## Create a Fork

Since we are a member of our co-learner’s project we could create a merge
request within the project. But again, to learn how to do it for project’s of
which we are not a member of, we will make ourselves some extra work.

So supposedly, we cannot make changes to our co-learner’s project. We need a
copy that we can change. Such a copy is called a fork in GitLab’s (and also
GitHub’s case). The term can be explained by looking at its use in “fork in the
road”. Once we make changes to our copy, the development history will have
split.

To create a fork, we navigate to the homepage of our co-learner’s project. In
the upper right corner is a button labeled ”Fork”. The number next to it tells
us how many forks of this repository exist on GitLab. We will now increase that
number by one by clicking on the button.

This redirects us to a form that looks like a reduced version of the “Create new
project” form. Since we do not want to make a real fork of the project, that is
project that develops in a different direction than the original, but rather
suggest a change to the original, we will leave almost everything as it is.

What we need to do is select a namespace. We will use our user namespace, so we
select ourselves in the drop-down list under ”Project URL”. We set the
visibility to private, because we will make the changes public (to those able to
see the original project) once we create the merge request. Then we click the
“Fork project” button.

::: callout

### Unique Project Name

If there already is a project with the name or the same slug, GitLab will show
you an error message which, at the time of me writing this, can be summarized to
“an error has occurred”, which is not very helpful. In that case, reload the
page, select a different name and/or slug and try again.

:::

We are redirected to the fork’s project home page. The fork is full featured
project just like the original, however, only the Git repository is copied. So,
for example, there are no issues in it, even though the original had at least one.

## Create and Edit a File on GitLab

Our goal is to create a file listing contributors to the project. We will do
this within GitLab using its file creation and editing features.

To do that, we click on the button labeled “Web IDE” in the line just below the
project’s description. This redirects us to a page with a file browser in a
column on the, with most of the screen taken up by a box informing us how to use
the Web IDE: “Select a file from the left sidebar to begin editing. Afterwards,
you’ll be able to commit your changes.”

We do not want to edit an existing file, but want to create a new one. To do
that we click on the button above the list of files on the left that is marked
with an icon representing a sheet of paper with a +-sign on top of it.

A pop-up dialog prompts us for a name, which we will provide: “CONTRIBUTORS.md”
followed by clicking the button labeled “Create file”.

::: callout

### All caps filenames

In software projects it is customary to name certain files with information
about a project in all caps. One example we already encountered is the README
file. Others are the file containing the license (`LICENSE`), a file about how
to contribute (`CONTRIBUTING`), or how to install the software (`INSTALL`).

Sometimes a file extension indicating the format is appended, usually in
lower-case letters.

:::

We see the result of our action in two ways: A file named “CONTRIBUTORS.md”
appeared in the list of files on the left and a tab labeled “CONTRIBUTORS.md”
showing an text editor appeared in the space to the right of the list of files.

We will now add something similar the following lines in the editor:

```markdown
The following persons have contributed to my research diary:

- Conner Learner
```

Then we click the button labeled “Create a commit”. The view to the left of the
list of files gets split into to columns. On the left side we see the old
version of the file (it did not exist, so nothing is shown) and on the right
side we see the new version with additions marked in green. If we had removed
anything from the old version those lines would have been marked red on the left
side.

Since everything looks as expected—one new file with called “CONTRIBUTORS.md”
with the lines we just typed in—we change the commit message to

```
Add CONTRIBUTORS.md
```

 We keep “Create a new branch” with the pre-generated name selected. For our
purposes we could also leave the checkbox “Start a new merge request” selected,
but we want to go through the merge request creation process separately to get
familiar with it, in case we want to create one from changes we pushed from a
local repository.

We do create a new branch and do not commit the changes to the branch called
“main”, because it is a good habit. We might want to create multiple independent
merge requests for one project, which cannot be done from a single branch. And
then there is the option to create merge requests within a project, those cannot
come from the branch they are supposed to be merged to, so we need another
branch anyway.

Finally, we click the button labeled “Commit”.
