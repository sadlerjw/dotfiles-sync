dotfiles-sync
=============

Scripts to sync your dotfiles (or any other configurations) to Git, in order to keep them up to date between computers.
Invoking these scripts will automatically pull down changes from your `origin` remote, commit all your changes, and push everything back up to `origin`.
This is really useful to help sync your fork of [mathiasbynens/dotfiles](https://github.com/mathiasbynens/dotfiles/) (or Paul Irish's [fork](https://github.com/paulirish/dotfiles/))

Installation
------------
Just drop these files somewhere into your path. I like to keep mine in `~/bin/` because then I can use these very scripts to keep it up-to-date in my dotfiles repo.

It's also a good idea to set up aliases for any configuration repos you set up (see below). For example:
`alias sync-sublime="sync-git \"~/Library/Application\ Support/Sublime\ Text\ 2/Packages/User/\""`

Usage
-----
###Sync Aribtrary Config Files to a Git Repo using `sync-git`

1.  Create a new Git repository in the folder that contains your configuration files. For instance, if you want to sync your Sublime Text 2 configuration between multiple Macs, create a new repo in `~/Library/Application Support/Sublime Text 2/Packages/User`
2.  Make sure that your repository is set up with an `origin` remote, which is where these scripts will automatically push your changes. (The script also assumes you're working on your `master` branch)
3.  `sync-git [path to your repo]`

###Sync Files Living in Your Home Directory
You probably don't want to create a Git repository right in your home directory, so `sync-dotfiles` allows you to create a repo elsewhere (it assumes `~/dotfiles`) and have it sync files from your home directory to the repo, pull remote changes, commit local changes, sync the merged files back into your home directory, and then push all changes back up to `origin`.

**NB**: `sync-dotfiles` only includes files from your home directory that *already exist* in your `~/dotfiles` repo, but syncs *all* files from `~/bin`.

1. Create a new Git repository in `~/dotfiles`.
2. Copy any files you want to keep in sync from your home directory into `~/dotfiles`.  For example, to keep your `.bashrc` in sync, copy it to `~/dotfiles/.bashrc`; to keep a file in `~/a/b/file` synced, copy it to `~/dotfiles/a/b/file`.
3. Commit your changes.
4. `sync-dotfiles`
