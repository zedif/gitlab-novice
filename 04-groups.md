---
title: "Groups"
teaching: 0
exercises: 0
---

::: questions

- How can I organize the projects of my (research) group and my collaborations?

:::

::: objectives

- Create a group.
- Move a project.
- Add a member to a group.
- Explain how the members of a group relate to its subgroups and projects.
- Delete a group.

:::

In the first episode, we already got to know groups; GitLab’s way to organize
projects. A group might hold a projects of a research group or those of a
research project with contributors from multiple institutions.

In this episode we will create (and delete) a group, move our project, and learn
how members of a group relate to its subgroups and projects.

## Creating a Group

In the top menu bar, we open the drop-down menu labeled with a boxed plus and
select the menu item “New Group”. On the next page, we select “Create group”,
because that is what we want to do.

This leads to the following page:

![Create form dialog](fig/create-group.png){alt="Create group form with text
input fields labeled “Group name”, “Group URL”, a radio button element labeled
"Visibility Level” with options “Private” and “Public”, a drop-down field
labeled “Role”, a radio button element labeled “Who will be using this group?”
with options “My company or team” and “Just me”, a drop-down field labeled “What
will you use this group for?” and an text input field labeled “Email 1” with a
button to add more under the heading “Invite members (optional)”."}

Choose any name for the group, for example a fictional research group like
“Ant-Sized Elephants’ Applications Lab”. When you move the focus out of the
input field, for example by pressing the tabulator key, GitLab will suggest a
URL for the group. Usually, we might want to adapt it, but for now all we care
about that it is available.

You can leave the group’s visibility private. The visibility of a group works
like that of a project.

We will leave the remaining fields as they are and create the group by clicking
the blue button labeled “Create group”. GitLab will navigate to the group home
page, listing the group’s subgroups and projects (currently none).

Now, we will have a look at how to create a project in the new group.

In the top menu bar, we open the drop-down menu labeled with a boxed plus and
select the menu item “New Project”. On the next page, we select “Create blank
project”.

This leads to the create blank project form page. We do not really want to
create a project. Instead we have a look at the drop-down field under the
heading “Project URL”. It will either show your username or one of the groups
you belong to.

If the field does not show the URL of the group that we just created, clicking
on the field should open a drop-down list which includes it and allows us to
select it.

Submitting the form with our group’s URL selected would create a project in that
group.

## Move Project to Group

We will now move our project to our group.

On the side menu, we select “Settings” then “General”. On that page, we expand
the section labeled “Advanced” and scroll down to the subsection labeled
“Transfer Project”.

Now, please read the subsections notes, with an emphasis on the list of things
to be aware of.

A few comments on the last two items of the list:

The second to last tells us that we will need to update our local repositories
to point to the new location. Because we are moving the project to a group from
our own projects, the URL will change. So the URL we specified when adding the
remote to our local repository will no longer be valid. We will test this, but
will not change the URL, because we will move the project back in a bit.

The last item on the list informs us about potential visibility changes. For
example, moving a public project to a private group, will cause the project to
become private.

Having carefully read and thought about the warnings, we are ready to move our
project. We select the group that we previously created from the drop-down field
and click the button labeled “Transfer project”.

A dialog appears and we confirm, that we are sure, by typing in the name of our
project and clicking the button labeled “Confirm”.

The project will be transferred to the group.

To test that the URL changed, we switch to the shell and navigate to the
directory containing our repository; **Not the repository of our co-learner**!

Running

```
git remote get-url origin
```
{: .language-bash}

should tell us that our project points to the old project URL. So, let us try to
run

```
git pull
```
{: .language-bash}
```
Already up to date.
```
{: .output}

That result is unexpected. The reason for this is that [GitLab will redirect the
old URLs to the new ones, as long as the old URLs do not point to a new
project.][GitLab-Redirect]

[GitLab-Redirect]: https://docs.gitlab.com/ee/user/project/repository/#what-happens-when-a-repository-path-changes

