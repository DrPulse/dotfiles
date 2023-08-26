# dotfiles

Your dotfiles are how you personalize your system. These are mine.

As of now I use [chezmoi](https://www.chezmoi.io/) to sync my dotfiles accross machines. This repository contains my dotfiles in the format chezmoi needs them, but they can be renamed and work right out of the gate.

Here is a summary of how chezmoi works.

## Installation and setup

This will install chezmoi

```sh
sh -c "$(wget -qO- get.chezmoi.io)"
```

Append `-- init --apply $GITHUB_USERNAME` to install chezmoi AND apply the files of the user's repository if it's named `dotfiles`.

Then run `chezmoi init` to create a local git repository for chezmoi to use.

## Files management

### Base commands

To add any file run `chezmoi add $FILE`.
The file will be copied in the chezmoi directory.

To remove chezmoi managed file run `chezmoi remove $FILE` and type `y`.

`chezmoi managed` will list everything managed by chezmoi.

`chezmoi unmanaged` will list everything not managed by chezmoi. You can add entire directories with chezmoi add.

`chezmoi diff` shows  what changes chezmoi would make

`chezmoi -v apply` apply the changes

### Edit files

You can edit a file in many ways:

- `chezmoi edit $FILE`
- `chezmoi cd` and edit the file
- edit the source file and run `chezmoi add $FILE` or `chezmoi re-add`
- edit the source file and run `chezmoi merge $FILE`

I find chezmoi re-add to be better, especially when changing multiple files, but it doesn't happen frequently.

### Commit the files

For your first or any file changement, the logic stays the same, add files and commit them to git.

```sh
chezmoi cd
git add .
git commit -m "Initial commit"
```

On your first commit, add the remote repository.

```sh
git remote add origin https://github.com/$GITHUB_USERNAME/dotfiles.git
git branch -M main
```

And push the changes.

```sh
git push -u origin main
```

Note: if you fail to pull or fetch the repository, run `git pull --rebase` to move the ref heads and update your local repository without causing a divergence in the remote repository.
