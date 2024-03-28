+++
title="The git page"
date=2024-02-19
draft=false
[taxonomies]
tags=["the-page"]
+++

# Force pushes

There is a safer force-pushing option called `--force-with-lease`.
It checks to make sure what you last pushed is still the latest server version before forcing a branch update.
If it isn't, the command will fail with the "stale info" error.

You can set up an alias of `git push` for this with

```sh
$ git config --global alias.fpush push --force-with-lease
```

Or just use it like

```sh
$ git push --force-with-lease
```

# Security

## Sign commits with SSH

You can sign data using your existing SSH key.
GitHub and GitLab support verifying these signatures if you upload your public signing key to your user account.

Set `gpg.format` to `ssh` and tell it where your signing key is

```sh
$ git config gpg.format ssh
$ git config user.signingKey ~/.ssh/id_rsa.pub
```

Running `git commit -S` will sign your commit with this key.

## Sign pushes

Git allows you to sign pushes as well as commits.[^ChaconSign]

None of the major Git hosting solutions support this, but if they do, run

```sh
$ git push --signed
```

To sign the ref update on the server and have the server save a transparency log with verifiable signatures somewhere.[^Ryabitsev]

# Automate stuff

## Add cronjobs for maintenance on your git repo

`git maintenance` allows you to add daily, hourly, and weekly tasks for your repositories.
Turn it on for a repository by running

```sh
$ git maintenance start
```

This modifies your `.git/config` file to add a `maintenance.strategy` value set to `incremental`.
`incremental` is a shorthand for:

- `gc`: disabled
- `commit-graph`: hourly
- `prefetch`: hourly
- `loose-objects`: daily
- `incremental-repack`: daily

Every hour it will rebuild your commit graph and do a prefetch, and once a day it will clean up loose files into pack-files and repack the object directory using the multi-pack-index.
These features are really helpful when working with large projects.


# Git configs

Git has a key/value store called `git config` which will check in three places for values:

- _locally (in the project)_ at `.git/config`
- _globally (for the user)_ at `~/.gitconfig`
- _system-wide_

You can specify the value you are changing using the syntax

```sh
$ git config [--global | --system | --local] root.key "Value"
```

If you add to your global config the following

```
[includeIf "gitdir:~/project/path"]
    path = ~/.gitconfig-oss
```

Then Git will look in the `~/.gitconfig-oss` file for values only if the project you are working in matches `~/project/path`.
You can also filter by branch name using `onbranch` or if the project matches a specific URL using `hasconfig:remote.*.url`.


# git blame

The line range option (`-L`) allows you to display a subsection of the file

```sh
$ git blame -L 28,43 path/to/file
```

The `:` syntax allows Git to find the beginning of a block and only blame that block

```sh
$ git blame -L :'class LocalFile' path/to/file
```


## Following

`git blame` can ignore whitespace changes to see the real person changing the code using the `-w` option.

The `-C` option allows you to look for code movement between files in a commit.
It will follow refactoring of functions from one file to another, showing the last person to actually change certain lines of code.
You can pass `-C` up to three times to follow code even harder.

```sh
$ git blame -w -C -C -C
```


# git diff

You can change Git's command-line `git diff` tool to be word-based rather than line based with the `--word-diff` option.


## Memorize and resolve conflicts automatically

Use the `rerere` option to have git remember the resolutions of conflicts automatically.

```sh
$ git config --global rerere.enabled true
$ git config --global rerere.autoUpdate true
```

`autoUpdate` stages the automatic resolution for you!


## Sorting branches

To show branches in sorted order in `git branch`, we can configure the `branch.sort` option by

- `objectsize`
- `authordate`
- `committerdate`
- `creatordate`
- `taggerdate`

Or by using the `--sort` option.

```sh
$ git config --global branch.sort -committerdate
```

specifies the descending committerdate order (`-` is negative)

You can display the branches in columns using the `column.ui` option

```sh
$ git config --global column.ui auto
```

Or with the `--column N` option.

# References

[^Chacon]: Scott Chacon, _Git Tips and Tricks_, Published 2024-02-14, [[Online]](https://blog.gitbutler.com/git-tips-and-tricks/)

[^ChaconSign]: Scott Chacon, _Signing Commits in Git, Explained_, Accessed 2024-02-19, [[Online]](https://blog.gitbutler.com/signing-commits-in-git-explained/)

[^Ryabitsev]: Konstantin Ryabitsev, _Signed git pushes_, Published 2020-11-03, [[Online]](https://people.kernel.org/monsieuricon/signed-git-pushes)

[^GitConfig]: The Git Project, _git-config Documentation_, Version 2.43.2, [[Online]](https://git-scm.com/docs/git-config)

[^StoleePacked]: Derrick Stolee, _Git's database internals I: packed object store_, Published 2022-08-29, [[Online]](https://github.blog/2022-08-29-gits-database-internals-i-packed-object-store/)
