# Contributing



The best way to contribute to the roadmap and feature discussions is by talking with the RSQUARELABS Team and 
rsquarelabs-core Community in realtime through the Gitter chat, or by starting a [new issue](https://github.com/rsquarelabs/rsquarelabs-core/issues/new) as a discussion thread.

- [Got a Question or Problem](#gaqp)
- [Browsing the code](#code)
- [Found a Bug](#bug)
- [Want a feature](#want-feature)
- [Contributing to the project](#contributing-to-the-project)
    - [Setting the Dev Env](#setting-dev-env)
    - [Testing](#testing)
    - [Compatibility Issues](#compatibility-issues)
    - [Writing Documentation](#writing-documentation)
    - [Submitting a Pull Request](#submitting-pullrequest)
- [Submission Guidelines](#guidelines)
	- [Submitting an issue](#submit-issue)
	
- [Git Commit Guidelines](#commit-guidelines)
- [Code of Conduct](#code-of-conduct)
 
## <a name="gaqp"></a> Got a question or problem?

Search for your question or problem in the [existing issues](https://github.com/rsquarelabs/rsquarelabs-core/issues) or 
create a [new issue](https://github.com/rsquarelabs/rsquarelabs-core/issues/new) to start a new discussion thread. 

## <a name="code"></a>Browsing the code?

We work on two branches: 

- `master` for stable, released code

- `dev`, a development branch. 

It might be important to distinguish them when you are reading the commit history 
searching for a feature or a bugfix, or when you are unsure of where to base your work from when contributing.

  


##<a name="bug"></a>Found a bug?
We would like to hear about it. Please [submit an issue][#submitting-an-issue] on GitHub and we will follow up. Even better, we would appreciate a [Pull Request][new-pr] with a fix for it!

- If the bug was found in a release, it is best to base your work on `master` and submit your PR against it.
- If the bug was found on `dev` (the development branch), base your work on `dev` and submit your PR against it.

Please follow the [Pull Request Guidelines][#submitting-a-pull-request].  
  

##<a name="want-feature"></a> Want a feature?

Feel free to request a feature by [submitting an issue][new-issue] on GitHub and open the discussion.

If you'd like to implement a new feature, please consider opening an issue first to talk about it. It may be that somebody is already working on it, or that there are particular issues that you should be aware of before implementing the change. If you are about to open a Pull Request, please make sure to follow the [submissions guidelines][new-pr].



## <a name="contributing-to-the-project"></a>Contributing to the project
 

1. Fork the `rsquarelabs/framework` repository! 
2. Clone the repository to your local machine. 
3. Select an issue from [rsquarelabs/framework](https://github.com/rsquarelabs/rsquarelabs-core/issues?q=is%3Aopen) to work on or 
[submit a proposal](https://github.com/rsquarelabs/rsquarelabs-core/issues/new) of your own.
4. Create a feature or hotfix, or fix  branch depending on the type of issue.
5. Write the `tests` needed, take care of Python 2 & 3 compatibility issues. 
6. Modify existing or add new `.md` files to the docs directory.
7. As you work, build the documentation site locally to see your changes using `mkdocs serve`.
8. Check your writing for style and mechanical errors.
9. Squash your commits on your branch.
10. Make a pull request from your fork back to  `master` branch.
11. Work with the reviewers until your change is approved and merged.


### <a name="setting-dev-env"></a>Setting the Dev Env

To start developing on rsquarelabs/framework, clone the repo:
From the root of the repository:

```bash
# Clone the project
git clone git@github.com:rsquarelabs/framework.git

# Create the virtual environment
virtualenv venv

# Install requirements
venv/bin/pip install -r requirements/dev-requirements.txt

# Activate the environment
source venv/bin/activate

# Access the commands
python sbin/r2_gromacs.py init # for gromacs module
python sbin/r2_server_start # start the webclient in localhost

```

**Note:** You do not need a database or to run migrate.

All the changes should broadly follow the [PEP 8](https://www.python.org/dev/peps/pep-0008/) style conventions, 
and we recommend you set up your editor to automatically indicate non-conforming styles.


### <a name="testing"></a>Testing 

1. Write tests for all the code that you write, which includes writing the unittests to integration tests. 
2. Always try to test the compatibility with Python versions 2x and 3x.


### <a name="compatibility-issues"></a>Compatibility Issues

Sometimes, in order to ensure your code works on various different versions of R2-Core framework, 
Python or third party libraries, you'll need to run slightly different code depending on the environment. 
Any code that branches in this way should be isolated into the `compat.py` module, 
and should provide a single common interface that the rest of the codebase can use.


### <a name="writing-documentation"></a>Writing Documentation

The documentation for R2-Core framework is built from the [Markdown](https://guides.github.com/features/mastering-markdown/) source files in the 
`docs` directory.

There are many great Markdown editors that make working with the documentation really easy. Test the documentation by seeing 
your changes using `mkdocs serve`. You should be able to access the documentation locally at [http://localhost:8000](http://localhost:8000)


### <a name="submitting-pullrequest"></a>Submitting a Pull Request


The pull request (PR) process is in place so that we can ensure changes made to the 
codes are the best changes possible. A good PR will do some or all of the following:

1. Explain why the change is needed
2. Point out potential issues or questions
3. Ask for help from experts in the company or the community
4. Encourage feedback from core developers and others involved in creating the software being documented.
5. Check if the code is Python 2 & 3 compatible. 

Writing a PR that is singular in focus and has clear objectives will encourage all of the above. 
Done correctly, the process allows reviewers (maintainers and community members) 
to validate the claims of the documentation and identify potential problems in communication or presentation

- First of all, make sure to base your work on the `dev` branch (the development branch):   a bugfix branch for dev would be prefixed by `fix/`
  # a bugfix branch for master would be prefixed by `hotfix/`

  ```
  $ git checkout -b feature/my-feature dev
  ```

- Please create commits containing **related changes**. For example, two different bugfixes should produce two separate commits. A feature should be made of commits splitted by **logical chunks** (no half-done changes). Use your best judgement as to how many commits your changes require.

- Write insightful and descriptive commit messages. Also add the issue number to make more sense for the issue.
 Please provide a summary in the first line (50-72 characters) along with the issue number `#<issue_number>` in the commit message.
 
- Please **include the appropriate test cases** for your patch.

- Make sure all tests pass before submitting your changes. See the [Makefile operations](/README.md#makefile-operations).

- Make sure the linter does not throw any error: `make lint`.

- Rebase your commits. It may be that new commits have been introduced on `dev`. Rebasing will update your branch with the most recent code and make your changes easier to review:

  ```
  $ git fetch && git rebase origin/dev
  ```

- Push your changes:

  ```
  $ git push origin -u feature/my-feature
  ```

- Open a pull request against the `dev` branch.

- If we suggest changes:
  - Please make the required updates (after discussion if any)
  - Only create new commits if it makes sense. Generally, you will want to amend your latest commit or rebase your branch after the new changes:

    ```
    $ git rebase -i dev    # choose which commits to edit and perform the updates
    ```

  - Re-run the test suite
  - Force push to your branch:

    ```
    $ git push origin feature/my-feature -f
    ```



Once you've made a pull request take a look at the `Travis build status` in the GitHub interface and make sure 
the tests are running as you'd expect.
GitHub's documentation for working on pull requests is [available here](https://help.github.com/articles/using-pull-requests/).



### <a name="submit-issue"></a>Submitting an issue

Before you submit an issue, search the archive, maybe you will find that a similar one already exists.

If you are submitting an issue for a bug, please include the following:

- An overview of the issue
- Your use case (why is this a bug for you?)
- The version of rsquarelabs-core you are running
- The platform you are running rsquarelabs-core on
- Steps to reproduce the issue
- Logfiles if available are helpful.
- Ideally, a suggested fix
 

##<a name="commit-guidelines"></a>Git Commit Guidelines
We have very precise rules over how our git commit messages can be formatted. This leads to more readable messages that are easy to follow when looking through the project history. But also, we use the git commit messages to generate the AngularJS change log.

The commit message formatting can be added using a typical git workflow or through the use of a CLI wizard ([Commitizen](https://github.com/commitizen/cz-cli)). To use the wizard, run npm run commit in your terminal after staging your changes in git.

Every Commit must be one of the following Type :


* **feat**: A new feature
* **fix**: A bug fix
* **docs**: Documentation only changes
* **style**: Changes that do not affect the meaning of the code (white-space, formatting, missing
  semi-colons, etc)
* **refactor**: A code change that neither fixes a bug nor adds a feature
* **perf**: A code change that improves performance
* **test**: Adding missing tests
* **chore**: Changes to the build process or auxiliary tools and libraries such as documentation
  generation
  
  
  

## <a name="code-of-conduct"></a>Code of Conduct

We follow the code of conduct by [contributor-covenant.org](http://contributor-covenant.org/version/1/3/0/)





------


We are eager to see your contribution!

We collect all requests and ideas and share with the community for feedback, you should watch the milestones and issues for further roadmap updates.