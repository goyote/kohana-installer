# Kohana Installer

The `ko` cli script helps you automate (and thus eliminate) the redundant steps that you need to take in order to install Kohana successfully through either the console by means of a git repo or by going to the official website and downloading the zip file manually.

http://www.youtube.com/watch?v=PgdQR_uPm0s

## Installation

For global access by all users, move the `ko` file into `/usr/bin`.

     wget https://raw.github.com/goyote/kohana-installer/master/ko -P /usr/bin/
     chmod 0755 /usr/bin/ko

Now all users get access to `ko`, login and type `ko` on the command line to see the help screen or type `ko install` to see something happen.

## Usage

Open a shell and specify a command to run:

**install**: Installs Kohana by downloading the latest zip file from the official website.

    $ ko install                                  <- Downloads Kohana to "./kohana"
    $ ko install --name=myapp                     <- Downloads Kohana to "./myapp"
    $ ko install --path=my/other/dir              <- Downloads Kohana to "./my/other/dir/kohana"
    $ ko install --path=my/other/dir --name=myapp <- Downloads Kohana to "./my/other/dir/myapp"
    $ ko install --mode=755                       <- Uses mode "755" instead of "777" for new files/dirs

*Note*: When using --path, if a dir does not exist, it will be created.

*Note*: When using --path, the permissions on existing dirs will not get overridden (by design.)

***

**git**: Sets up a new git repo, adding the Kohana modules as git submodules.

    $ ko git                               <- Sets up a new repo in "./kohana"
    $ ko git --name=myapp                  <- Sets up a new repo in "./myapp"
    $ ko git --path=other/dir              <- Sets up a new repo in "./other/dir/kohana"
    $ ko git --path=other/dir --name=myapp <- Sets up a new repo in "./other/dir/myapp"
    $ ko git --mode=755                    <- Uses mode "755" instead of "777" for new files/dirs
    $ ko git --modules=orm,database        <- Installs only the orm and database modules (the default is all official ones)
    $ ko git --tag=3.1                     <- index.php, bootstrap.php and .htaccess are fetched with this tag, submodules default to master branch

Installation based on the official guide: http://kohanaframework.org/3.2/guide/kohana/tutorials/git

***

**skeleton**: Builds a skeleton of dirs for sharing Kohana between multiple projects.

    $ ko skeleton                              <- Creates the dirs "./{projects,kohana,modules}"
    $ ko skeleton --name=apps                  <- Creates the dirs "./{apps,kohana,modules}"
    $ ko skeleton --path=other/dir             <- Creates the dirs "./other/dir/{kohana,kohana,modules}"
    $ ko skeleton --path=other/dir --name=apps <- Creates the dirs "./other/dir/{apps,kohana,modules}"
    $ ko skeleton --mode=755                   <- Uses mode "755" instead of "777" for new files/dirs

More information @ http://kohanaframework.org/3.2/guide/kohana/tutorials/sharing-kohana

***

**system**: Downloads the "system" directory from GitHub (may be used in conjunction with skeleton.)

    $ ko system              <- Clones github.com/kohana/core (master branch) into "./system"
    $ ko system --tag=v3.1.0 <- Clones github.com/kohana/core and checks out tag "v3.1.0" into "./3.1.0"
    $ ko system --mode=755   <- Uses mode "755" instead of "777" for new files/dirs

***

**modules**: Downloads all the official modules form GitHub (may be used in conjunction with skeleton.)

    $ ko modules                        <- Clones all the official modules into "."
    $ ko modules --path=modules         <- Clones all the official modules into "./modules"
    $ ko modules --modules=orm,database <- Clones only the orm and database modules into "."
    $ ko modules --mode=755             <- Uses mode "755" instead of "777" for new files/dirs

***

**fix**: Fixes some shitty defaults.

    $ ko fix  <- Renames example.htaccess to .htaccess, removes install.php and makes cache/logs writable

*Important*: Make sure you cd into the dir that contains the index.php, or provide a --path to it.
