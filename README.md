## PS1TD zsh customizations

### Step 1: Install ZSH

```
sudo apt install zsh
```

```
sudo chsh -s $(which zsh)
```

### Step 2: Fonts

[Fira Code](https://github.com/tonsky/FiraCode) Font
[MesloLGS NF](https://github.com/romkatv/powerlevel10k#fonts) Font

After downloading install all ttf fonts
Set MesloLGS NF to be used by Terminal

### Step 3: Set up Oh My Zsh

```
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

Log out and log back in
Open Terminal and go through set up process

### Step 4: Set theme to powerlevel10k

```
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k
```

Set ZSH_THEME="powerlevel10k/powerlevel10k" in ~/.zshrc
Relaunch Terminal and go through customization

### Step 5: Plugins

In ~/.zshrc set

```
plugins=(git zsh-autosuggestions sudo history docker kubectl-autocomplete)

# zsh-autocomplete
fpath+=${ZSH_CUSTOM:-${ZSH:-~/.oh-my-zsh}/custom}/plugins/zsh-completions/src

# Docker completion style
zstyle ':completion:*:*:docker:*' option-stacking yes
zstyle ':completion:*:*:docker-*:*' option-stacking yes

```

Install zsh-autosuggestions

```
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
```

Install zsh-autocomplete

```
  git clone https://github.com/zsh-users/zsh-completions ${ZSH_CUSTOM:-${ZSH:-~/.oh-my-zsh}/custom}/plugins/zsh-completions
```

Install zsh-syntax-highlighting
```
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
```

Install fast-syntax-highlighting
```
git clone https://github.com/zdharma-continuum/fast-syntax-highlighting.git \
  ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/plugins/fast-syntax-highlighting
```

Install Docker Completions

```
mkdir -p ~/.oh-my-zsh/plugins/docker/
curl -fLo ~/.oh-my-zsh/plugins/docker/_docker https://raw.githubusercontent.com/docker/cli/master/contrib/completion/zsh/_docker
```

Install Kubectl Completions
```
mkdir -p ~/.oh-my-zsh/custom/plugins/kubectl-autocomplete/
kubectl completion zsh > ~/.oh-my-zsh/custom/plugins/kubectl-autocomplete/kubectl-autocomplete.plugin.zsh
```
```
# use autocompletion
autoload -Uz compinit
compinit

# change according to completions source
source <(kubectl completion zsh)
alias k=kubectl
compdef k=kubectl

# for microk8s kubectl
microk8s.kubectl() {
    microk8s kubectl "$@"
}
alias mk="microk8s.kubectl"
compdef microk8s.kubectl=kubectl
compdef mk=kubectl
```

### Step 6: Aliases

```
alias k="kubectl"
alias mk="microk8s kubectl"
alias gc="gcloud"
```

### Step 7: Environment Variables

```
export KUBE_EDITOR="nano"

# Git
export GPG_TTY=$(tty)

# .NET
export PATH=$PATH:$HOME/.dotnet
export DOTNET_ROOT=$HOME/.dotnet

# PNPM
export PNPM_HOME="/home/ps1td/.local/share/pnpm"
case ":$PATH:" in
  *":$PNPM_HOME:"*) ;;
  *) export PATH="$PNPM_HOME:$PATH" ;;
esac

# NVM
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"  # This loads nvm bash_completion

# Yandex CLI
if [ -f '/home/ps1td/yandex-cloud/path.bash.inc' ]; then source '/home/ps1td/yandex-cloud/path.bash.inc'; fi

if [ -f '/home/ps1td/yandex-cloud/completion.zsh.inc' ]; then source '/home/ps1td/yandex-cloud/completion.zsh.inc'; fi

```

And others...

### Step 8: Root

Repeat steps 3,4,5,6 & 7 while being root

```
sudo su
```
