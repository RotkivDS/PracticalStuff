# PracticalStuff
## Bundleing
``npx esbuild index.ts --bundle --outfile=dist/bundle.js --format=esm --target=es2020``

## Mac

```xattr -dr com.apple.quarantine /Applications/Easy\ Move+Resize.app```

https://github.com/dmarcotte/easy-move-resize

### Mouse
```defaults write .GlobalPreferences com.apple.mouse.scaling -1```

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
## `systemD` Stuff

### Services and Timer
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

```
# /etc/systemd/system/certbot-renewal.service
[Unit]
Description=Certbot Renewal
[Service]
ExecStart=/usr/local/bin/certbot -q renew --post-hook "systemctl reload nginx"

# /etc/systemd/system/certbot-renewal.timer
[Unit]
Description=Run certbot twice daily

[Timer]
OnCalendar=*-*-* 00,12:00:00
RandomizedDelaySec=43200
Persistent=true

[Install]
WantedBy=timers.target

```

### `@` Sign in services
Note: Some unit names contain an @ sign (e.g. name@string.service): this means that they are instances of a template unit, whose actual file name does not contain the string part (e.g. name@.service). string is called the instance identifier, and is similar to an argument that is passed to the template unit when called with the systemctl command: in the unit file it will substitute the %i specifier. To be more accurate, before trying to instantiate the name@.suffix template unit, systemd will actually look for a unit with the exact name@string.suffix file name, although by convention such a "clash" happens rarely, i.e. most unit files containing an @ sign are meant to be templates. Also, if a template unit is called without an instance identifier, it will generally fail (except with certain systemctl commands, like cat).

### Restart and apply changes
```
systemctl daemon-reload
systemctl restart bla.service
```

## PaperlessNGX
In Container: python3 manage.py createsuperuser

## PaperlessNGX
InkStitch for Stiching files

## Keras multi input and output
https://keras.io/guides/functional_api/
