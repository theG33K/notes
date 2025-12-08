No Thumbnails

It has something to with the way tumbler and DBus interact. To fix it, You have to manually start tumbler. For example, YOu need to edit your WM/DM startup file. For example in openbox, Edit ~/.config/openbox/autostart and put this line 
```bash
/usr/lib/tumbler-1/tumblerd &
