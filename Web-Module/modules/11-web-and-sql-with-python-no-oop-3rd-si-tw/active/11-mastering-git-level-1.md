# Mastering git - level 1

![gitflow-01.png](media/Web%20with%20Python%20module%20resources/gitflow-01.png)

As you already know, Git is an extremely powerful tool (with an awful user interface :-) ). It has to be really mastered, in order to be able to use the best parts of it.

You already know how to add, commit and push your changes. You write nice commit messages (aren't you?), and in case you forget something, you know how to modify your last commit. You also know how to pull code from others, and fix the possible merge conflicts as a pro.

To simplify things: you're already semi-professional in git, but there are few things you should master to be able to call yourself a pro!

## Branching

Some of you already had the need to be able to work on their functionality, without having to pull other's changes continuosly, causing merge conflicts, loosing valuable time from the real work. This is why branching has been invented.

### Branching / merging

Branching means you diverge from the main line of development and continue to do work without messing with that main line. You've already used a branch, without your knowledge: whenever you committed your changes to git, you always did that to the branch called _master_.

Please read and understand the following articles about branching:

<https://git-scm.com/book/en/v2/Git-Branching-Branches-in-a-Nutshell> (3.1-3.7, use the 'next' links in the bottom)

<https://www.atlassian.com/git/tutorials/using-branches>[LINK](https://www.atlassian.com/git/tutorials/using-branches)

When you get the basic understanding about branching, please do the following interactive tutorial's first chapter ( _Main/Introduction sequence_ ):

<http://learngitbranching.js.org>

Please do the following interactive tutorial as well:

<https://try.github.io/levels/1/challenges/1>

### Branching workflows

Branching is all about handling massive collaboration issues. But it's worthless, without using a workflow, in which the rules are kept by all participants.

Please read and understand the following articles about branching workflows, and about some de-facto rules about how to contribute to a project:

<https://www.atlassian.com/git/tutorials/comparing-workflows>

[optional] <https://git-scm.com/book/en/v2/Distributed-Git-Distributed-Workflows>

[optional] <https://git-scm.com/book/en/v2/Distributed-Git-Contributing-to-a-Project>

## Handling pull requests on GitHub

GitHub is an awesome platform sitting on the top of their hosted git service, adding incredible features which ease the life of any developers. Since many company use GitHub, nearly all of the open-source projects are hosted on GitHub, moreover, you use GitHub, it's worth checking one of it's best feature, called pull requests.

Please read and understand the following article about pull requests:

<https://help.github.com/articles/using-pull-requests/>

## How will we use this knowledge?

We gonna use Gitflow Workflow from the next TW week, so please make sure you understand how should it look like!

## And when can I be sure?

You can be sure about your knowledge, if you can answer the following questions:

  * What is git and what is a repository? _(seriously, can you explain these to a non-IT person?)_
  * What does it mean to clone a repository?
  * What does it mean to fork a repository?
  * What is a branch in git? How to create it? _(there are multiple ways)_
  * What happenes if you have commited your changes into a development branch and you checkout the master? Where is the development changes are stored?
  * What is a tag? Where is it stored? Can you commit it? Do you need to push/pull it?
  * What is a merge commit? How the default commit message looks like?
  * What is HEAD? What does it mean if it's detached?
  * What is a pull request? Is it a git feature?


