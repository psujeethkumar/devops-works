# Linux workstation setup

## Beautifying terminal

1. Install zsh shell
```
sudo dnf install zsh

```
2. Change the shell default to zsh
```
chsh -s $(which zsh)
```
3. Log-off and log back in into the server, start the terminal. It will prompt for initial settings for the zsh. 
   Follow the select the options according to the preferences.
4. Install Oh-My-Zsh
```
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```
5. Install Powerlevel10k custom theme. 
6. Configure oh-my-zsh to use Powerlevel10k theme by editing the .zshrc file in the profile folder.
```
vim .zshrc

ZSH_THEME="powerlevel10k/powerlevel10k"

```
7. Source the changes and follow applying the settings prompted by the theme.
```
source .zshrc
```
8. Install following plugins: 
     autosuggestion 
     zsh-syntax-highlighting plugin
     zsh-fast-syntax-highlighting plugin
     zsh-autocomplete plugin
```
git clone https://github.com/zsh-users/zsh-autosuggestions.git $ZSH_CUSTOM/plugins/zsh-autosuggestions

git clone https://github.com/zsh-users/zsh-syntax-highlighting.git $ZSH_CUSTOM/plugins/zsh-syntax-highlighting

git clone https://github.com/zdharma-continuum/fast-syntax-highlighting.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/plugins/fast-syntax-highlighting

git clone --depth 1 -- https://github.com/marlonrichert/zsh-autocomplete.git $ZSH_CUSTOM/plugins/zsh-autocomplete

```
9. Enable plugins in .zshrc file
```
plugins= (
            git 
            zsh-autosuggestions 
            zsh-syntax-highlighting 
            fast-syntax-highlighting 
            zsh-autocomplete
          )
```
