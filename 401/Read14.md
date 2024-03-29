# Data Visualization

## Matplotlib Tutorial

- matplotlib is probably the single most used Python package for 2D-graphics.
- Some tools:
  1. iPython - Interactive Python shell
  2. pyplot - Interface for matplotlib plotting library
- Some Simple Plots:
```
Lines:
Line color: plt.plot(X, C, color="blue")
Line width: plt.plot(X, S, linewidth=2.5)
Line style: plt.plot(X, S, linestyle="-")
Spacing:
plt.xlim(X.min()*1.1, X.max()*1.1)
plt.ylim(C.min()*1.1, C.max()*1.1)
Ticks:
plt.xticks( [1, 2, 3, 4, 5])
plt.yticks([1, 2, 3])
plt.set_xticklabels([])
plt.set_yticklabels([])
Legend: 
plt.legend(loc='upper left', frameon=False)
```
- Figures, Subplots, Ticks:
```
plt.figure(): Create a figure, optional params:
  -num: Number it
  -figsize: size in inches (w, h)
  -dpi: resolution
  -facecolor: background
  -edgecolor: edge
  -frameon: Draw frame or not
plt.subplot(x, y, index): create subplot
```
- Other Plots:
```
Regular: Lines and/or markers
Scatter: Scatter X versus Y
Bar: Bar plot
Contour plot: Contour lines and filled contours
Imshow: Plot an image
Quiver Plot: 2D field of arrows
Pie chart: Pie of an array
Grid: Ticks and grid
Multiplot: Serveral splots at once
Polar Axis: Plot using polar axis
3D Plots: 2D or 2D data
Text: Draw any kind of text
```