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
plugins=(git zsh-autosuggestions sudo history docker kubectl)

# Docker Autocompletions
zstyle ':completion:*:*:docker:*' option-stacking yes
zstyle ':completion:*:*:docker-*:*' option-stacking yes

``` 

Install zsh-autosuggestions
```
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
```

### Step 6: Environment Variables
```
# Git
export GPG_TTY=$(tty)

# .NET
export PATH=$PATH:$HOME/.dotnet
export DOTNET_ROOT=$HOME/.dotnet

# PNPM
export PNPM_HOME="/home/ps1td/.local/share/pnpm"
export PATH="$PNPM_HOME:$PATH"

# NVM
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"  # This loads nvm bash_completion
```
And others...

### Step 7: Root
Repeat steps 3,4,5 & 6 while being root
```
sudo su
```
