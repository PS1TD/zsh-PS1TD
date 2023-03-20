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

### Step 2: Install [Fira Code](https://github.com/tonsky/FiraCode) Font
```
https://github.com/tonsky/FiraCode
```

### Step 3: Set up Oh My Zsh
```
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

### Step 4: Set theme to powerlevel10k
```
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k
```
