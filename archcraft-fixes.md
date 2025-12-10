No Thumbnails

It has something to with the way tumbler and DBus interact. To fix it, You have to manually start tumbler. For example, You need to edit your WM/DM startup file. For example in openbox, Edit ~/.config/openbox/autostart (or the applicable rc file) and add this line 
```bash
/usr/lib/tumbler-1/tumblerd &
