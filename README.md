# Welcome to the Sentenial GitHub Pages Documentation

## Prerequisites
- Install docker on your machine
- Install git for your operating system
- If you are required to use a proxy the following environment variables are observed.
  - http_proxy url of your http proxy 
  - https_proxy url of your https proxy
  - no_proxy csv list of addresses to not use the proxy for

## Documentation Workflow

The following details how to create a pull request for this repo.
1) Fork the repository https://github.com/sentenial/developer-docs *[Once Off Step]*
2) git clone the new fork, an example is shown below this will however be pointing to your fork. *[Once Off Step]*
```
git clone https://github.com/whelanp/developer-docs.git
```
3) Add a link to the upstream repository you forked from. *[Once Off Step]* (sometimes this is called the remote upstream maintainer URL).
```
git remote add upstream https://github.com/sentenial/developer-docs.git
```
4) create a feature branch for your edits and switch to your feature branch, sample command shown below
```
git checkout -b my-feature
```
5) In the project there is a docker compose file run the following to start up a Jekyll docker container. The compose file is called *docker-compose.yml*
```
docker-compose build --no-cache && docker-compose up
```
6) Work on the changes you wish to make to the project
7) Commit your change to the feature branch you created in step 4 when you are happy with the changes. docker runs Jekyll on localhost:4000 you can observe the changes you make in the browser at this URL. Once you are happy with the changes you can commit them.
```
git commit -m "my commit message".
```
8) Switch back to you master branch
```
git checkout master
```
9) Get updates from the upstream master, this could of changed since you created your fork of the repository.
```
git pull upstream master
```
10) Push these changes to our origin master branch
```
git push origin master
```
11) Switch back to your feature branch
```
git checkout my-feature
```
12) Rebase off local master, this brings into the branch any updates on the master branch we may of missed. (sometimes there will be no changes that's fine too)
```
git rebase master
```
13) Push the change to origin master
```
git push origin my-feature
```
14) Login to the user interface and create a pull request. After you have created a pull request the Maintainers of the project decide to accept or reject the pull request.

TODO add pictures
