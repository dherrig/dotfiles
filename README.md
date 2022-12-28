# dotfiles
## Setup 
### New system, existing repo
```shell
echo 'alias dotfiles="/usr/bin/git --git-dir=$HOME/.dotfiles.git/ --work-tree=$HOME"' >> $HOME/.bashrc
source ~/.bashrc
echo ".dotfiles.git" >> .gitignore
git clone --bare git@github.com:dherrig/dotfiles.git $HOME/.dotfiles.git
dotfiles checkout
dotfiles config --local status.showUntrackedFiles no
```

### From scratch
```shell
git init --bare $HOME/.dotfiles.git
echo 'alias dotfiles="/usr/bin/git --git-dir=$HOME/.dotfiles.git/ --work-tree=$HOME"' >> $HOME/.bashrc
source ~/.bashrc
dotfiles config --local status.showUntrackedFiles no
dotfiles remote add origin git@github.com:dherrig/dotfiles.git

```

## Using the repo
Use the `dotfiles` alias (created during setup) where `git` would normally be used. E.g.
```shell
dotfiles status
dotfiles add ~/.vim/vimrc
dotfiles commit -m "update vimrc"
dotfiles push origin main
```

## Credits
* https://www.atlassian.com/git/tutorials/dotfiles
* https://harfangk.github.io/2016/09/18/manage-dotfiles-with-a-git-bare-repository.html
