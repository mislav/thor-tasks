Thor tasks
==========

Getting started: install [Thor](http://github.com/wycats/thor/tree/master) if you haven't.

    gem install wycats-thor

You can install these tasks directly from Web or, if you clone the repo, from the filesystem:

    # install from Web
    thor install http://github.com/mislav/thor-tasks/tree/master/github.thor?raw=true
    # from local file
    thor install github.thor

Thor will ask you to name your import. You can later use this name to update installed tasks:

    thor update GitHub

On update, Thor will try to fetch the tasks from the same source you specified during install.

If you want to inspect and try out the tasks **without** installing, you should clone the repo:

    git clone git://github.com/mislav/thor-tasks.git
    cd thor-tasks
    thor list

This command will get you a list of tasks together with their usage information.

And now for a bit of fun.    


GitHub tasks
------------

Imagine the most common GitHub scenario: somebody forked your project, and now you want to pull changes from it. This is where the `track` task comes in:

    github:track mislav

A `remote add`, `fetch` and tracking branch creation happens behind the scenes:

    git remote add mislav git://github.com/mislav/repo-name.git
    git fetch --no-tags mislav master:refs/remotes/mislav/master
    git branch mislav --track mislav/master

Saved us a lot of typing, didn't it? The `create` task is even better:

    github:create new-repo

This asks you for your GitHub login, sends out a HTTP request to create a new repository and creates this setup:

    git remote add origin git@github.com:user/new-repo.git
    git push origin master
    git config branch.master.remote origin
    git config branch.master.merge refs/heads/master

Uploading your project to GitHub has never been quicker!