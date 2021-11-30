# lb
Terminal application for displaying slectable menu based on lines from the standard input.
User can pipe arbitrary lines to **lb** for making a selectable menu with quick search capability.

Example how to create selectable menu displayed in terminal for quickly copying passwords:
```bash
lpass show -cp $(lpass ls -l | lb | sed 's/.*id: \([0-9]*\).*/\1/g')
```
