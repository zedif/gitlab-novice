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
feature on GitHub is called Pull Request.

As a target for our merge request, we will use our co-learners repository. We
we have write access to it, but to learn something new, we will pretend that we
don’t.

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
as we can notice, there are no issues in it, even though the original had at
least one.
