Our Git process is an upgraded version of [Github Flow](https://guides.github.com/introduction/flow/).

![](https://ftp.infinum.co/stjepan_hadjic/git-flow-2.jpg)

Instead of a single `master` branch, we use two branches to record the history of the project. The `master` branch stores code that's currently in production. The `staging` branch serves as an integration branch for features and fixes. It holds data that reflects what's currently on staging.

**The master branch is always deployable.**

As we use [Productive](https://productive.io) to manage our tasks, we use **feature branches** for fixes and new features. Our branch naming convention is {type}/{task-number}{descriptive-task-name}. For example, a branch for adding authentication would be named `feature/123-authentication`.

*Types*
* _feature_ - new feature or an improvement to an existing feature
* _fix_ - non-critical bugfix, improvement, paying the technical debt. Goes through code review process
* _hotfix_ - time sensitive critical bugfix, that should be deployed to production as soon as possible. Not necessary that it goes through code review, but it should be revisited at a later stage, and properly fixed or improved

Feature branches are **always** branched out of `master`. They are also merged first into `staging`, and then into `master` if they are ready for production.

**Never branch out of the `staging` branch and never merge `staging` into `master`**

## Why you need the `staging` branch and why you should never merge it into `master`
We use the `staging` server so that our QA team could test our applications in an environment that is as close to production as possible. We can also work on multiple features in parallel. Those fixes and features need to be verified by our QA team and sometimes by the client as well. Sometimes, a feature may be ready for production while others aren't and are still being worked on. In that case, the `staging` branch contains multiple features, but only one needs to end up on `master`. That is why we do not branch out of `staging` and do not merge `staging` into `master`.

## Note on workflow during early development:
While the application is still not deployed on a production server, you can omit the `staging` branch. Once the production server has been set up, and the first deploy has been up, create a `staging` branch.

## Other important notes on using Git:
**Commit messages are important**, especially since Git tracks your changes and then displays them as commits once they've been pushed to the server. By writing clear commit messages, you can make it easier for other people to follow and provide feedback.
Commits should have a descriptive subject as well as a quick explanation of the reason for the change in the commit body. This makes it easier to check changes in the code editor as you do not have to find the pull request and open it on github.
Read more about writing proper commit messages [here](http://chris.beams.io/posts/git-commit/).

**Make small commits, following the Single Responsibility Principle in Git.** This makes commits easier to review when making pull requests, and it's easier to notice what's going on when something goes wrong.

**Don't use `git add .`** Review what you're adding to your repo—this is the #1 cause of making unwanted changes.