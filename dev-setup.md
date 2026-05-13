# Development Setup

* Check out my dotfiles: https://github.com/cspetterson/dotfiles

### Terminal

I'm currently using a 16" Macbook Pro

* Font size: 14
* Window size: 200x58

### Generate new SSH key

From Github settings: https://github.com/settings/keys

* Follow these steps from Github: https://docs.github.com/authentication/connecting-to-github-with-ssh
* Add public key to authorized keys in dotfiles: https://github.com/cspetterson/dotfiles/blob/master/ssh/authorized_keys.pub

### Install Homebrew

Double check command at: https://brew.sh/

```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

### Clone dotfiles

Copy aliases, nvim & tmux settings, etc

* Trying to use a git command will suggest installing developer tools, do this

```
git clone https://github.com/cspetterson/dotfiles ~/.dotfiles
cd ~/.dotfiles
rake install
```

### Tab completion

https://oliverspryn.blog/adding-git-completion-to-zsh-60f3b0e7ffbc

TODO: This is in the dotfiles, does it need downloading?

```
# Download the scripts
curl -o ~/.dotfiles/zsh/git-completion.bash https://raw.githubusercontent.com/git/git/master/contrib/completion/git-completion.bash
curl -o ~/.dotfiles/zsh/_git https://raw.githubusercontent.com/git/git/master/contrib/completion/git-completion.zsh
```

Following has already been added to ~/.zshrc

```
zstyle ':completion:*:*:git:*' script ~/.dotfiles/zsh/git-completion.bash
fpath=(~/.dotfiles/zsh $fpath)
autoload -Uz compinit && compinit
```

## Setup list

### ASDF

https://github.com/asdf-vm/asdf

Following steps from the Getting Started guide: https://asdf-vm.com/guide/getting-started.html

Check they are up to date

Install dependencies:

```
brew install coreutils curl git gpg gawk
```

Install ASDF:

```
brew install asdf
```

### Ruby

Versions: https://www.ruby-lang.org/en/downloads/releases/

```
asdf plugin add ruby
asdf install ruby latest
asdf global ruby latest
gem update --system
```

### Node

Versions: https://nodejs.org/en/download/releases

```
asdf plugin add nodejs
asdf install nodejs latest
asdf global nodejs latest
```

### Yarn

Versions: https://github.com/yarnpkg/yarn/releases

```
asdf plugin-add yarn
asdf install yarn latest
asdf global yarn latest
```

### PostgresQL

Versions: https://www.postgresql.org/support/versioning/

```
brew install libpq postgresql
brew services start postgresql
```

### AI

**Claude**

https://code.claude.com/docs/en/overview#homebrew

```
brew install --cask claude-code
```

**Copilot**

https://docs.github.com/en/copilot/how-tos/copilot-cli/set-up-copilot-cli/install-copilot-cli`

```
brew install copilot-cli
```

### Neovim

Plugins are managed by [lazy.nvim](https://github.com/folke/lazy.nvim) and will auto-install on first launch. Config is included in dotfiles and symlinked to `~/.config/nvim` by `rake install`.

**ripgrep:** https://github.com/BurntSushi/ripgrep

Required for Telescope live grep (`,s`)

```
brew install ripgrep
```

**Nerd Font**: (I use "Hack") https://github.com/ryanoasis/nerd-fonts#option-2-homebrew-fonts

For icons in Neovim. Standard font is SF Mono, switching to Hack Nerd Font.

```
brew install font-hack-nerd-font
```

Remember to change the font in terminal settings -> profiles -> font

### ctags

For `ctrl+]` file jumps

```
brew install ctags
```

Make sure to run `:!ctags -R --languages=ruby --exclude=.git --exclude=log . $(bundle list --paths)` (dotfiles shorthand: `,ct`) in projects

### Tmuxinator

https://github.com/tmuxinator/tmuxinator

```
gem install tmuxinator
brew install tmuxinator
```

**TODO**: Setup standard tmux project in dotfiles

### Standard Gems

```
gem install bundler rails
```
