# Code in Grayscale World

Polychrome is evil.

## Monochrome System
To convert linux system to grayscale, we might need `picom` or `compton`.
### Prerequisite
#### picom (Best so far)
```bash
# picom (better than compton, performance-wise)
# dependencies
sudo apt install -y libxext-dev libxcb1-dev libxcb-damage0-dev libxcb-xfixes0-dev libxcb-shape0-dev libxcb-render-util0-dev libxcb-render0-dev libxcb-randr0-dev libxcb-composite0-dev libxcb-image0-dev libxcb-present-dev libxcb-xinerama0-dev libxcb-glx0-dev libpixman-1-dev libdbus-1-dev libconfig-dev libgl1-mesa-dev libpcre2-dev libpcre3-dev libevdev-dev uthash-dev libev-dev libx11-xcb-dev meson
# Clone with ssh
git clone --recursive git@github.com:yshui/picom.git
# Clone with https
`git clone --recursive https://github.com/yshui/picom.git
# Build
meson --buildtype=release . build
ninja -C build
# Install
ninja -C build install
```
#### compton (Slower than picom)
```bash
sudo apt install compton
git clone https://github.com/bubbleguuum/toggle-monitor-grayscale
edit toggle-monitor-grayscale.sh
```
### toggle-monitor-grayscale.sh
This script converts your whole system into grayscale.
https://github.com/bubbleguuum/toggle-monitor-grayscale
```bash
git clone https://github.com/heeh/toggle-monitor-grayscale
edit toggle-monitor-grayscale.sh
./toggle-monitor-grayscale
```
## Monochrome Terminal
Linux .bashrc file usually contains ls --color and this makes directory hard to read. Let's override this.
### .dircolor
```bash
#.dircolors
LK                    0
CAPABILITY            0
CHR                   0
DIR                   1
DOOR                  0
EXEC                  0
FIFO                  0
FILE                  0
LINK                  0
MULTIHARDLINK         0
# "NORMAL don't reset the bold attribute -
# https://github.com/trapd00r/LS_COLORS/issues/11
#NORMAL                38;5;254
NORMAL                0
ORPHAN                0
OTHER_WRITABLE        0
SETGID                0
SETUID                0
SOCK                  0
STICKY                0
STICKY_OTHER_WRITABLE 0
```

## Monochrome Editor
### emacs 
#### White background
```lisp
;; Set background color to #FFFFFF
customize-face
```
https://sachachua.com/blog/2009/01/emacs-basics-changing-the-background-color/
#### monochrome-theme
```lisp
;; For emacs, this is the best theme.
M-x package-install monochrome-theme
```

### Intellij Idea
https://github.com/abrookins/kant

## Monochrome Browser
### firefox 
It it hard to tell if the text is a link or not. The following css uses underline for this.
- Go to `about:profile`
- Create `<profile>/chrome/userChrome.css`
```css
/* userChrome.css */
a {
    color: #000000 !important;
    background-color:transparent !important; /* necessary so link is always readable */
    text-decoration: underline !important; 
}  /* Unvisited link color */

a:visited {
    color: #7f7f7f !important;
    background-color:transparent !important; /* necessary so link is always readable */
    text-decoration: underline !important; 
}   /* Visited link color */
```
## Monochrome Terminal
### alacritty
https://clcode.net/articles/color-schemes.md
.config/alacritty/allacritty.yml
```bash
env:
  TERM: xterm-mono
  # TERM: xterm-256color
  # TERM: alacritty-direct

#Font
font:
  normal:
    family: Cascadia Code
    style: Light
  bold:
    family: Cascadia Code
    style: Regular
  italic:
    family: Cascadia Code
    style: Light Italic
  bold_italic:
    family: Cascadia Code
    style: Regular Italic
  size: 10

# Colors (Terminal.app Basic)
colors:
  primary:
    background: "#FFFFFF"
    foreground: "#000000"
  normal:
    black:      "#000000"
    red:        "#990000"
    green:      "#00A600"
    yellow:     "#999900"
    blue:       "#0000B2"
    magenta:    "#B200B2"
    cyan:       "#00A6B2"
    white:      "#BFBFBF"
  bright:
    black:      "#666666"
    red:        "#E50000"
    green:      "#00D900"
    yellow:     "#E5E500"
    blue:       "#0000FF"
    magenta:    "#E500E5"
    cyan:       "#00E5E5"
    white:      "#E5E5E5"

# Cursor 
cursor:
  # Cursor style
  style:
    # Cursor shape
    #
    # Values for `shape`:
    #   - ▇ Block
    #   - _ Underline
    #   - | Beam
    shape: Block

    # Cursor blinking state
    #
    # Values for `blinking`:
    #   - Never: Prevent the cursor from ever blinking
    #   - Off: Disable blinking by default
    #   - On: Enable blinking by default
    #   - Always: Force the cursor to always blink
    blinking: Never
    blink_interval:   75
```
### Monochrome File Manager
midnight commander with seasons-winter16M works fine so far.  
```sudo apt install mc```
