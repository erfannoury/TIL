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

----

To display images sequentially on the desktop without the need to manually close the display windows, use the following line:
```python
interval = 0.1  # in seconds
for img in images:
    # ... some codes
    plt.imshow(img)
    
    plt.show(block=False)
    plt.pause(interval)
    plt.close()
```

[Source](https://stackoverflow.com/questions/40395659/view-and-then-close-the-figure-automatically-in-matplotlib#comment68078694_40395799)

----
To solve the `DLL Error` when importing `matplotlib` (specifically this error happens when importing `ft2font` from `matplotlib`) first uninstall the matplotlib installed using conda (`conda uninstall matplotlib`) and then install it using pip (`pip install matplotlib`). Also before installing with pip, make sure to remove matplotlib's folder from `site-packages`.
