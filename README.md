# My dotfiles

## To add this config to your system:

```bash
git clone --bare https://github.com/andredp/dot-files.git $HOME/.cfg
function config {
   /usr/bin/git --git-dir=$HOME/.cfg/ --work-tree=$HOME $@
}
mkdir -p .config-backup
config checkout
if [ $? = 0 ]; then
  echo "Checked out config.";
  else
    echo "Backing up pre-existing dot files.";
    config checkout 2>&1 | egrep "\s+\." | awk {'print $1'} | xargs -I{} mv {} .config-backup/{}
fi;
config checkout
config config status.showUntrackedFiles no

```

### Alternatively you can do:
```bash
curl -Lks https://gist.github.com/andredp/554faa5ea94c0267aa5cf6698a004ab4#file-cfg-install-sh | /bin/bash
```

## After that you can do stuff like:

```bash
config add file1
config commit -m "Add file1"
config push 
```

## Things you might want to install on a fresh system:
- Awesome Vim: https://github.com/amix/vimrc
- zsh + prezto: https://github.com/sorin-ionescu/prezto
- Homebrew: https://brew.sh/
- diff-so-fancy: https://github.com/so-fancy/diff-so-fancy
- iTerm2: https://www.iterm2.com/ (Point it to read the configuration file in $HOME)
- Source Code PRO: https://github.com/adobe-fonts/source-code-pro

#### This dotfiles repo was inspired by: https://developer.atlassian.com/blog/2016/02/best-way-to-store-dotfiles-git-bare-repo/

