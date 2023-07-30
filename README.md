# PracticalStuff

## HEIC Convert 
```
mogrify -quality 85% -format jpg -path ./jpgs *.HEIC &
```
## Matlibplot
Working latex preamble stuff
```
import matplotlib.pyplot as plt

 plt.rc('text', usetex=True)
 plt.rc('text.latex', preamble=r'\usepackage{amsmath} \usepackage{foo-name}')
```
Set custom Latex Markers for stem plots
```
markerline, stemlines, baseline = ax.stem(sx, sy, sz)
markerline.set_marker(r"$\text{\normalfont\sun}$")
markerline.set_markersize(10)
```
Latex Font Fix
```
plt.rcParams.update({
    "text.usetex": True,
    "font.family": "sans-serif",
    "font.sans-serif": "Helvetica",
})
```
##systemD Stuff

```
ln -s /path/to/timers/timer-exec-stuff.service /etc/systemd/system/timer-exec-stuff.service
systemctl enable timer-exec-stuff.service
systemctl start timer-exec-stuff.service

ln -s /path/to/timers/timer.timer /etc/systemd/system/timer.timer
systemctl enable rclone-pipemaze.timer
systemctl start rclone-pipemaze.timer

```

`timer.timer`
```
[Unit]
Description=Stuff

[Timer]
OnBootSec=1min
OnUnitActiveSec=1d
Unit=%i.service

[Install]
WantedBy=timers.target
```

`timer-exec-stuff.service`
```
[Unit]
Description=Stuff Service
Wants=timer.timer

[Service]
Type=oneshot
ExecStart=/path/to/exec.sh

[Install]
WantedBy=multi-user.target
```
