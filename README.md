# AwesomeConfig

https://gist.github.com/e7b04f775233ed7e2ead390d30c12d9f.git

## Preprocess

```
sudo apt install zsh
sudo chsh -s $(which zsh) <username>
bash -c "$(curl --fail --show-error --silent --location https://raw.githubusercontent.com/zdharma-continuum/zinit/HEAD/scripts/install.sh)"
```

## zshrc

```
zinit ice as"command" from"gh-r" \
          atclone"./starship init zsh > init.zsh; ./starship completions zsh > _starship" \
          atpull"%atclone" src"init.zsh"
zinit light starship/starship

# syntax highlight
zinit ice lucid wait='0' atinit='zpcompinit'
zinit light zdharma/fast-syntax-highlighting

# auto suggest
zinit ice lucid wait="0" atload='_zsh_autosuggest_start'
zinit light zsh-users/zsh-autosuggestions

# auto complete
zinit ice lucid wait='0'
zinit light zsh-users/zsh-completions

# conda
zinit ice lucid wait='0'
zinit light esc/conda-zsh-completion

# git
zinit snippet OMZ::lib/git.zsh
zinit ice lucid wait="0" atload="zpcompinit; zpcdreplay"
zinit snippet OMZ::plugins/git/git.plugin.zsh

# 加载 OMZ 框架及部分插件
zinit snippet OMZ::lib/clipboard.zsh
zinit snippet OMZ::lib/completion.zsh
zinit snippet OMZ::lib/history.zsh
zinit snippet OMZ::lib/key-bindings.zsh
zinit snippet OMZ::lib/theme-and-appearance.zsh

# oh-my-zsh plugins
zi light-mode wait lucid for \
    OMZ::plugins/git/git.plugin.zsh \
    OMZ::plugins/pip/pip.plugin.zsh \
    OMZ::plugins/python/python.plugin.zsh \
    OMZ::plugins/history/history.plugin.zsh \
    OMZ::plugins/autojump/autojump.plugin.zsh \
    OMZ::plugins/gitignore/gitignore.plugin.zsh \
    OMZ::plugins/common-aliases/common-aliases.plugin.zsh

[ -f ~/.fzf.zsh ] && source ~/.fzf.zsh
```
