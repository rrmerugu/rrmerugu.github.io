---
layout: post
title:  "Setting up Continuous testing and Continuous Integration(CI) with Jenkins in localhost"
---


Jenkins is one of the coolest open-source tool. As a developer I write many codes
in a day and performs many commits, pulling the code a day. I like
[Travis CI](https://travis-ci.org/) for opensource projects, but when it comes to
private projects they charge me. So I was exploring Jenkins and realised that's what
I want for my localhost.

<!--/excerpt-->


**Continuous testing** is the process of executing automated tests as part of the software delivery pipeline to obtain immediate feedback on the business risks associated with a software release candidate. (Source: Wiki)

**continuous integration (CI)** is the practice of merging all developer working copies to a shared mainline several times a day. (Source: Wiki)


### Step1: Create a free style project

![Create a free style project](/public/img/jenkins/1.png)


### Step2: Configure settings

In this step, we will tell Jenkins, which `git` repository it should worry about.
In our case, .git project is in our machine. So `select` git as `Source Code Management` and
give the  absolute path of the git repository.

Specify the branch it should monitor, by default it will be `master`, but in continuous testing,
you might be worried about `develop` branch also, in that case give `*` in Branch Specifier.

![Configure settings](/public/img/jenkins/2.png)


### Step3: Setup Build Triggers

You can trigger a build by sending `Authentication Token` in a GET request of the url
`http://localhost:8080/job/challengeX/build?token=1234567890`.

![Setup Build Triggers](/public/img/jenkins/3.png)

Doing simple `curl http://localhost:8080/job/challengeX/build?token=1234567890` in the terminal
should trigger a build :D. But it's not over yet, so still need to tell jenkins how
to create a build.

### Step4: Configuring Build Process

In this step we will tell Jenkins, how to create a build and post build scripts.

![Configuring Build Process](/public/img/jenkins/4.png)
![Configuring Build Process 2](/public/img/jenkins/5.png)

If you want to run a script `npm run tests` in the shell, update the settings as mentioned above.


### Step5: Configure post-commit hook for git project


Now we need to tell when this test should trigger. Lets say, we want to trigger the
 build creation process on `post-commit`. You should add a `hook` to git project,
 something `<project_path>/.git/hooks/post-commit`. Copy the following lined into
 post-commit hook.

 ```
 #!/bin/sh
 echo "trigerring the post commit "
 curl http://localhost:8080/job/challengeX/build?token=1234567890
 ```

![Configure post-commit hook for git project](/public/img/jenkins/6.png)

Where `challengeX` is your project name.


### Step6: Tweak you Security Settings

This is need for making the http://localhost:8080/job/challengeX/build?token=1234567890 as
anonymous user. Go to http://localhost:8080/configureSecurity/  and check the `Allow anonymous read access` option.

![Tweak you Security Settings](/public/img/jenkins/7.png)


All set for continuous testing, When you perform a new commit, a new build will be triggered
and all the reports of the build generation, both success and failures can be found
from [http://localhost:8080/job/challengeX/](http://localhost:8080/job/challengeX/), where
`challengeX` is your project name.


## Jenkins UI
I'm not a fan of Jenkins UI, but there are plugins out there
that will change the skin of Jenkins :). http://arji.me/jenkins-neo-theme/ is
one the themes I found cool, but Im sure you can find much better themes.
