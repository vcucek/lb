# lb
Terminal application for displaying selectable menu based on lines from the standard input.
User can pipe arbitrary lines to **lb** for making a selectable menu with quick search capability.

List browser provides a similar functionality to the suckless dmenu, except that it is written in bash and displays selection menu in the terminal.
Consequently **lb** does not depend on X or any other graphical environment other then tty.

## Install

Copy lb script file to folder specified in the PATH environment variable. For example:
```bash
cp lb /usr/local/bin
```

## Example usages

1. Create a selectable menu for browsing and copying lastpass passwords:
```bash
lpass show -cp $(lpass ls -l | lb | sed 's/.*id: \([0-9]*\).*/\1/g')
```

2. Keyboard layout switcher:
```bash
setxkbmap $(printf 'SI\nUS' | lb | tr '[:upper:]' '[:lower:]' )
```

3. Browse system unit files and print status:
```bash
systemctl status $(systemctl list-units-files | lb | awk '{ print $1 }')
```

4. Browse history and execute:
```bash
eval $(cat ~/.bash_history | lb -l 30)
```

5. SSH to host specified in ~/.ssh/config
```bash
 ssh $(grep "^host" ~/.ssh/config | awk '{ print $2 }' | lb)
```
