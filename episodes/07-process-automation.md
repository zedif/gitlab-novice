---
title: "Process Automation"
teaching: 0
exercises: 0
---

::: questions

- How can I use GitLab to automate processes?

:::

::: objectives

- Setup a process to run automatically when a commit is pushed to a repository.
- Safely use secrets in a process automatically triggered by GitLab.

:::

We have setup our project, collaborated with our colleagues; we fill our
research diary every day. Now it is time to make use of it.

We think about using part of our daily commute by train to review what happened
in the past. We always have our e-reader with us, so ideally we would like to
have an version of our diary in EPUB format.

Just as much based in reality as the rest of this lesson’s story, we know how to
do that, but we do not want to do it by hand. Instead, we are going to let
GitLab automatically build us an EPUB file, whenever our repository changes. To
achieve it, we will us the feature that GitLab files under “CI/CD”, which stands
for Continuous Integration/Continuous Deployment.

::: callout

### Continuous Integration/Continuous Deployment

The terms continuous integration (CI) and continuous deployment (CD) come from the
fields of software engineering and software operation.

A software project uses CI, if it has setup a process that automatically runs
some (or all) tests for a software project, whenever changes are committed or
even just proposed (for example through a merge request) to the main branch of a
repository. In particular when already done for proposed changes this can help
prevent bugs to reach the code base, while freeing the developer of thinking of
and running all the tests themselves.

CD is a process that updates the software on the production machines (deploys)
as soon as a new change reaches the code base, generally after having passed the
CI process.

Both processes can be implemented by running scripts, called jobs, triggered
either by changes to the code base or by the successful completion of other
jobs, which lead to the CI/CD feature of GitLab.

:::

## Example Configuration

To configure our automatic process, we navigate to our project page and click
the menu item labeled  “CI/CD” in the main menu on the left.

The page that this leads to invites us to “use a sample `.gitlab-ci.yml`
template file to explore how CI/CD works.” The GitLab-CI is configured by
providing a file called `.gitlab-ci.yml` in the root directory of a project’s
repository. Even though we want to learn how CI works in GitLab, we do not
follow the invitation, because the example is quite elaborate and targets
software developers specifically. Instead, we will use the provided template for
Bash.

We click on the button labeled “Use template” of the entry for Bash in the list
at the bottom of the page.

This leads us to an editor for the `.gitlab-ci.yml` file that is prefilled from
the selected template. The file is expected to be written in the
[YAML](https://yaml.org/) file format, hence the file extension `.yml`. We will
go through the example line by line. Afterwards we will adapt it to our needs.

The first few lines, starting with the symbol `#`, are comments notifying us of
where to find further information. The last of these lines is the exception,
which is a comment on the first functional line:

```YAML
image: busybox:latest
```

This line states that the scripts that are provided later on should be executed
in Docker containers build from the stated Docker image. Busybox is a very small
Linux distribution, reduced to the bare minimum, and it provides a shell.

::: callout

### Docker

TODO

:::

Now follow to blocks starting with `before_script:` and `after_script:`. We will
ignore those.

The remaining four blocks, `build1:`, `test1:`, `test2:`, and `deploy1:`, each
define a so called job. A job defines a script and represents one non-divisible
unit of a CI/CD process. Together the jobs defined in a project’s
`.gitlab-ci.yml` file form a so called pipeline.

By default a pipeline has three stages, called `build`, `test`, and `deploy`,
and their order is important. The terminology comes from software development
again. A pipeline is executed by running all jobs of the first stage and if they
succeed to continue onto the next stage, continuing until a job fails or all
jobs of the last stage succeeded.

The four jobs in the example are named similar to the stages they are assigned
to. The assignment is done through the keyword `stage:` that can always be found
in the second line of a job’s definition.

The lines following the keyword `script:` in each section, define the script
that will be executed as part of the respective job. In this example, they are
all `echo` statements.

## Our Own Configuration

We will now adapt the script to our requirements.

First we delete everything.

Then we define our own stages, because we do not develop software and want to
have names for stages that fit:

```yaml
stages:
    - test
    - create
```

In the first stage, we will do some testing, in the second we will create an
EPUB format version of our research diary.

We call the first job `test-mds` and in it make sure, that at least one Markdown
file exists, because otherwise someone must have accidentally removed them all.

```yaml
test-mds:
    image: bash:latest
    stage: test
    script:
        - test -f *.md
```

We use the docker image `bash`, because Bash provides the `test` command and we
do not need anything else. We also state that the job belongs to the stage
`test`. Finally, we provide the script, which tests for the existence of files
with names ending in `.md`.

When this job succeeds we want to create the EPUB format version of our research
diary. We define a second job and call it `create-epub`.
