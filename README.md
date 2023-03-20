## PS1TD zsh customizations

### Step 1: Install ZSH
```
sudo apt install zsh
```
```
sudo chsh -s $(which zsh)
```
Log out and log back in
Open Terminal and press 2

### Step 2: Fonts
[Fira Code](https://github.com/tonsky/FiraCode) Font
[MesloLGS NF](https://github.com/romkatv/powerlevel10k#fonts) Font

After downloading install all ttf fonts
Set MesloLGS NF to be used by Terminal

### Step 3: Set up Oh My Zsh
```
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

### Step 4: Set theme to powerlevel10k
```
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k
```
Set ZSH_THEME="powerlevel10k/powerlevel10k" in ~/.zshrc
Relaunch Terminal and go through customization
