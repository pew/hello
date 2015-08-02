# dotfiles

```
git clone https://github.com/zsh-users/antigen .antigen

cat << EOF > $HOME/.zshrc
[ -e "${HOME}/.zsh_aliases" ] && source "${HOME}/.zsh_aliases"
[ -e "${HOME}/.zshrc_local" ] && source "${HOME}/.zshrc_local"

source "$HOME/.antigen/antigen.zsh"

antigen use oh-my-zsh

# bundles from oh-my-zsh
antigen bundle git
antigen bundle pip
antigen bundle rsync
antigen bundle python
antigen bundle zsh-users/zsh-completions src
antigen bundle zsh-users/zsh-syntax-highlighting
antigen bundle history
antigen bundle tmux

antigen-theme robbyrussell
antigen-apply
EOF
```
