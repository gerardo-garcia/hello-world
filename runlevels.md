# Runlevels #

## Mapping between runlevels and systemd targets ##

Runlevels:
- 0: poweroff.target
- 1: rescue.target
- 2,3,4: multi-user.target
- 5: graphical.target
- 6: reboot.target

## Change runlevel ##
To change runlevel now, e.g. to graphical:

`sudo systemctl isolate graphical.target`

## Set default runlevel ##
To set default runlevel, e.g. to multi-user.target:

```
sudo systemctl enable multi-user.target
sudo systemctl set-default multi-user.target
```


