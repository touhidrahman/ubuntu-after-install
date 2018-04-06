# If WPS Office doesn't launch (specially in KDE/Qt Environment)


Add `-style gtk+` to `/usr/bin/wpp`, `/usr/bin/wps`, and `/usr/bin/et` so it works from menu and file manager.

```
if [ 1 -eq ${gDaemon} ]; then
    nohup ${gInstallPath}/office6/${gApp} ${gOpt} -style gtk+ > /dev/null 2>&1 &
else
    ${gInstallPath}/office6/${gApp} ${gOptExt} ${gOpt} -style gtk+ "$@"
fi 
```
