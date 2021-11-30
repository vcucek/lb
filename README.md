# lb
Terminal application for displaying selectable menu based on lines from the standard input.
User can pipe arbitrary lines to **lb** for making a selectable menu with quick search capability.

List browser provides a similar functionality as dmenu, except that it displays selection in the terminal.
Consequently **lb** does not depend on X or any other graphical environment.

## Install

Copy lb script file to folder specified in the PATH environment variable. For example:
```bash
cp fb /usr/local/bin
```

## Example usages

1. How to create selectable menu displayed in terminal for quickly copying passwords:
```bash
lpass show -cp $(lpass ls -l | lb | sed 's/.*id: \([0-9]*\).*/\1/g')
```

2. Keyboard layout switcher:
```bash
setxkbmap $(printf 'SI\nUS' | lb | tr '[:upper:]' '[:lower:]' )
```

3. Display system unit files and print status:
```bash
systemctl status $(systemctl list-units | lb | awk '{ print $1 }')
```
