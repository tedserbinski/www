## About
- Source code to [tedserbinski.com](https://tedserbinski.com)
- Hosted on [👻](https://ghost.org)
- Theme forked from [Casper](https://github.com/TryGhost/Casper)


## Project Setup

### My setup had a few simple goals
- base my current theme off of the latest Casper release _(3.1.0 is what I started with)_
- merge in future bug fixes/updates from Casper to my theme _(especially API changes to maintain theme compatibility with major Ghost releases)_
- get Github contributions on my graph [(which don't work if you fork)](https://docs.github.com/en/github/creating-cloning-and-archiving-repositories/creating-a-repository-from-a-template)

After a few hours, I finally got this working. This was way harder than I thought. Or perhaps I'm just too rusty using Git (likely so, ha!). Huge thanks to [@Krystian](https://github.com/l0g1x) and [@Anthony](https://github.com/anthcor) for their guidance.

### End result
- I can develop my theme following easy and clear [git practices](https://githubflow.github.io)
- I've setup my [Ghost website to continuously deploy on commits to master](https://github.com/marketplace/actions/deploy-ghost-theme)
- I can compare the changes I've made to Casper with upstream changes and releases _(e.g., here's [all the custom changes I've made to Casper 3.1.0](https://github.com/tedserbinski/www/compare/casper-3.1.0...master))_
- Going forward, I plan to follow [this rebase technique to merge in changes](https://raygun.com/blog/git-workflow/) to Casper to my custom version
- I'll have to figure out how to create Pull Requests back to Casper if I fix bugs and/or add features. I'll leave that for another day :) _(likely I would have to fork Casper, copy my code changes from this repo into that one and submit as a pull request)_


## My Basic Approach

### Notes:
- I used the Github Desktop app to check and fix merge conflicts and push remotely
- If you can't login from the terminal, [see this blog post on how to setup access tokens](https://medium.com/@ginnyfahs/github-error-authentication-failed-from-command-line-3a545bfd0ca8)
- When it is time to merge in a new Casper release, I will:
```
git remote add upstream https://github.com/TryGhost/Casper.git
git checkout 3.x.y -b casper-3.x.y
git merge casper-3.x.y/master
git push
```

### Command flow:
1. Create a new Github project
2. Create a new branch "casper"
3. In the "casper" branch:
```
git remote add upstream https://github.com/TryGhost/Casper.git
git pull upstream master --allow-unrelated-histories
```
4. Create another branch with latest release:
```
git checkout 3.1.0 -b casper-3.1.0
````
5. Copy all files in this branch into master branch
6. Commit

### Helpful commands:
```
git fetch https://github.com/TryGhost/Casper.git master:casper
git checkout casper
git checkout master
git push
git rebase casper
git pull origin master —-allow-unrelated-histories
```
