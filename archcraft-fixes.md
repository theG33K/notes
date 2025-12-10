No Thumbnails

It has something to with the way tumbler and DBus interact. To fix it, You have to manually start tumbler. For example, You need to edit your WM/DM startup file. For example in openbox, Edit ~/.config/openbox/autostart (or the applicable rc file) and add this line 
```bash
/usr/lib/tumbler-1/tumblerd &
```

(BASE) Showing in terminals (after conda/miniconda install)

The conda activate in your shell rc file prepends your prompt with (<env-name->) - because you are not specifying a particular environment, that defaults to (base). The following command hides the (base) environment. Set the changeps1 to false in the condarc or run...
```bash
conda config --set changeps1 False
```
