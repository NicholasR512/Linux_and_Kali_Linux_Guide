## Purpose
Text editors are essential in Linux because many systems don’t have a GUI. In CTFs, you may need to open and edit files directly from the terminal. In the real world, sysadmins and penetration testers often edit configuration files, scripts, or logs using terminal-based editors.

## Core Commands
```bash
$ nano test.txt
#Opens "test.txt" in the Nano Text Editor | Ctrl+O to Save, Ctrl+X to Exit

$ vim test.txt
#Opens "test.txt" in Vim Editor | Press "i" to Insert, "Esc" to Exit Insert, ":wq" to Save & Quit

$ gedit test.txt
#Opens "test.txt" in Gedit GUI Text Editor (if installed)
```

!!! note "Editors Basics"  
	- `nano` is beginner-friendly, perfect for quick edits.  
	- `vim` is more powerful but has a steep learning curve.  
	- `gedit` is GUI-based, better when working in desktop environments.

### [[Linux Basics#12 - Editors|Editors Commands]]
