# lb
Terminal application for displaying selectable menu based on lines from the standard input.
User can pipe arbitrary lines to **lb** for making a selectable menu with quick search capability.

List browser provides a similar functionality as dmenu, except that it displays selection in the terminal.
Consequently **lb** does not depend on X or any other graphical environment.

Example how to create selectable menu displayed in terminal for quickly copying passwords:
```bash
lpass show -cp $(lpass ls -l | lb | sed 's/.*id: \([0-9]*\).*/\1/g')
```

Example keyboard layout switcher:
```bash
setxkbmap $(printf 'SI\nUS' | lb | tr '[:upper:]' '[:lower:]' )
```
