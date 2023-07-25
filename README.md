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
