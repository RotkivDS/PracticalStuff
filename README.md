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
