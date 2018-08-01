To set plot size for all plots in a notebook, use this command:
```python
from pylab import rcParams
rcParams['figure.figsize'] = 5, 10
```
> This makes the figure's width 5 inches, and its height 10 inches. 

Copied from [here](http://stackoverflow.com/questions/332289/how-do-you-change-the-size-of-figures-drawn-with-matplotlib)

----

When using matplotlib on a server to save figures, add the following two lines before import `pyplot`
```python
import matplotlib
matplotlib.use('agg')
```
[Source](https://stackoverflow.com/a/35737196/5069650)
