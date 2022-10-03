# Dotbot example

This uses [dotbot](https://github.com/anishathalye/dotbot) to bootstrap a new computer.

Be up and running in minutes rather than having to set all these tools up manually.

## Getting started

[Install homebrew](https://brew.sh/)

Clone this repository

```
git clone https://github.com/timja/dotfiles-example.git
```

Review the apps in `install.conf.yaml` and add any extras you want.

Run `./install`

### Configure apps

#### Starship

Starship is a nice terminal prompt tool follow it's [installation guide](https://starship.rs/guide) after the install script has been run.

#### GitHub CLI

Run `gh auth login`

This will ask you how you want to authenticate to GitHub and then prompt you to login to GitHub in the web browser and enter a code in your terminal.

#### Gitconfig

Ensure you setup your gitconfig or add it to your own fork of this repository.

`~/.config/git/config`:
```
[user]
	name = <your name>
	useConfigOnly = true
	email = <your email>
```

Consider signing your commits to prove it was you who authored them.
SSH signing is easier than GPG.

Follow the [GitHub documentation](https://docs.github.com/en/authentication/managing-commit-signature-verification/telling-git-about-your-signing-key#telling-git-about-your-ssh-key)

You need to add your SSH key to your ssh-agent with `ssh-add $ssh-key`.

If you configured the GitHub CLI to use SSH auth in the previous step you can use that for your signing key as well, just add it at [SSH and GPG keys](https://github.com/settings/keys).

### Casks

Make sure you open all the apps once from the casks section.
Rectangle and maccy will need accessibility permissions to work.

### Advanced usage

It's recommended that you fork the repository and add your own files, config and applications.

I have this at top of my `install.conf.yaml` which manages most of my dotfiles:

```yaml
- defaults:
    link:
      relink: true
      force: true

- clean: ['~']

- link:
    ~/.m2/settings.xml:
    ~/bin: bin
    ~/.config/:
      glob: true
      path: config/*
```