### My dotfiles

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

## After that you can do stuff like:

```bash
config add file1
config commit -m "Add file1"
config push 
```

## This dotfiles repo was inspired by: https://developer.atlassian.com/blog/2016/02/best-way-to-store-dotfiles-git-bare-repo/

