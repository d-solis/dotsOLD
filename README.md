# dots
# BSPWM | Polybar themes collection - Rice selector

## 🌿 Information
My dotfiles, 11 different rices for BSPWM and Polybar. With a Rice selector to change on the fly. 

https://user-images.githubusercontent.com/67278339/179444283-d5a4bc48-a9c7-4a91-a144-6c34d11347c8.mp4
 
## Rice Menu
<img src="assets/rs.webp" alt="Rice Menu" align="right" width="400px">

|DIstro|[Arch](https://archlinux.org/)|
|:---:|:---:|
|WM|[BSPWM](https://github.com/baskerville/bspwm)|
|Bar|[Polybar](https://github.com/polybar/polybar)|
|Menu|[Rofi](https://github.com/davatorium/rofi)|
|Compositor|[Picom Arian8j2](https://github.com/Arian8j2/picom)|
|Terminal|[Termite](https://aur.archlinux.org/termite.git)|
|Widgets|[ElKowars wacky widgets ](https://github.com/elkowar/eww)|

## 📖 Features
* **Change RICE on the fly:** 11 different Rices now!.

* **Rice Selector:** <code>Alt + Space bar</code> to launch it.

* **Random wallpaper:**  Every time you switch between rices or reload bspwm with <code>super + alt + r</code> a new wallpaper is set depending on the rice you are on.

* **Super + Alt + w** changes bethween different wallpapers in the actual rice.

* **Hide / Unhide Bar:** (Polybar)

* **Change transparency on the fly:** 
Increase and decrease transparency in focused or selected window.

## ⚠️ Attention!!
The rices work on my computer because they were made on my machine with my resolution (1600x900). They should also work on your computer, but you'll have to modify a lot of things to make them work for you.

</details>

## Very useful keybindigs to know...

|Action|Keybinding|
|---|---|
|Rice Selector|<code>alt + @space</code>|
|Menu|<code>super + @space</code>|
|Hide / Unhide Bar|<code>super + h / super + u</code>|
|Screenshot|<code>super + Print</code>|
|Transparency|<code>ctrl + alt {plus,minus,t}</code>|
|poweroff / Reboot|<code>ctrl + super + alt + {p,r}</code>|
|Terminal|<code>super + Return</code>|
|Brute Kill|<code>ctrl + super + alt + k</code>|
|Wallpaper Changer|<code>super + alt + w</code>|
|Restart bspwm|<code>super + alt + r</code>|

And more.. You need to look sxhkdrc file for more.

## 📦 setup

### 💾 Installation:
I will only provide instructions for arch based distributions.

<b>1. First of all we need yay and git</b>

```sh
pacman -S --needed git base-devel && git clone https://aur.archlinux.org/yay.git && cd yay && makepkg -si
```

<b>2. Install Dependencies: </b>

A one time command to install most of these dependencies with your **favorite AUR Helper** (we just install yay).

```sh
yay -S bspwm polybar sxhkd eww dunst rofi lsd jq checkupdates-aur \
playerctl mpd ncmpcpp mpc picom-arian8j2-git xtitle termite betterlockscreen \
ttf-jetbrains-mono nerd-fonts-jetbrains-mono nerd-fonts-terminus ttf-inconsolata \
ttf-joypixels nerd-fonts-cozette-ttf scientifica-font \
feh pamixer libwebp webp-pixbuf-loader xorg-xkill papirus-icon-theme
```

<b>3. Cloning Dotfiles & Installing:</b>
```sh
git clone --depth=1 https://github.com/gh0stzk/dotfiles.git

# ⚠️ Backuupp!! your filess!!!
[ -e ~/.config/bspwm ] && mv ~/.config/bspwm ~/.config/bspwm-backup-"$(date +%Y.%m.%d-%H.%M.%S)"
[ -e ~/.config/termite ] && mv ~/.config/termite ~/.config/termite-backup-"$(date +%Y.%m.%d-%H.%M.%S)"

# Moving new files to .config
cd dotfiles
cp -r config/bspwm ~/.config/bspwm
cp -r config/termite ~/.config/termite
# Those were the important ones. You still need to move the remaining directories in config to your ~/.config directory.

# Move Fonts and the other stuff
cp -r misc/fonts/* ~/.local/share/fonts/
cp -r misc/bin ~/.local/
cp -r misc/applications ~/.local/share/
cp -r misc/asciiart ~/.local/share/
fc-cache -rv

# You probably MUST use your own .zsh config, but if you want to use mine, do;
cp -r home/.zshrc ~/.zshrc
cp -r config/zsh ~/.config/zsh

# If you will not use my zsh config, just add to your .zshrc file, this;
if [ -d "$HOME/.local/bin" ] ;
  then PATH="$HOME/.local/bin:$PATH"
fi
```

<b>4. Enabling Services</b>
```sh
# For automatically launching mpd on login
systemctl --user enable mpd.service
systemctl --user start mpd.service
```
## Some tips

* Wallpapers are in .webp image format, i added libwebp webp-pixbuf-loader packages for your filemanager (thunar in my case) have the capacity to show webp thumbnails.
* If u dont wanna use the random wallpapers comment line 194 and uncomment line 195 from /home/YourUser/.config/bspwm/scripts/LaunchWorld file.
* Left click in pacman updates module in polybar to update. Right click for show updates available only.

## Troubleshooting
* **Bspwm Scripts or Launchers not responding**

The proper execute permissions on some files should be maintained when you download/clone and copy to your directories, but if not just run the following line by line.
```sh
chmod +x ~/.config/bspwm/bspwmrc
chown $USER ~/.config/bspwm/rice.cfg
chmod +x ~/.config/bspwm/scripts/{external_rules,hu-polybar,LaunchWorld,RiceSelector,screenshoter,updates.sh,weather-mini.sh}
# In Pamela & Andrea Rices, you need to give execution permissions to the shell scripts too.
chmod +x ~/.config/bspwm/rices/pamela/widgets/{calendar,calendarlauncher,getSongDuration,mplayer-launcher,music,power-launcher,profile-sys-launcher}
chmod +x ~/.config/bspwm/rices/andrea/arin/launch_bar
chmod +x ~/.config/bspwm/rices/andrea/arin/sidedar/toggle_sidebar
chmod +x ~/.config/bspwm/rices/andrea/arin/scripts/{battery,check-network,mails,music_info,quotes,sys_info,system,volume,weather_info,widget_apps,widget_search,workspaces.sh}
```
* Other

## Credits

https://github.com/gh0stzk/dotfiles
