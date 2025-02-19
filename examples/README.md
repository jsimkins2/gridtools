# Examples

This section explains the reasones for the
scripts and notebooks provided in this directory.

Running the examples may require adjustment to the
`wrkDir` variable to a directory.  This will allow
the example scripts can write sample output files.
Within that directory, you will need an `INPUT`
directory to simulate a MOM6 model runs input file
directory.

Some examples utilize the **GEBCO 2020** bathymetry.
The bathymetry will needed to be downloaded and scripts
edited for the storage location before they can be used.
See the [Bathymetry](../docs/resources/Bathymetry.md)
in the resources portion of the gridtools manual.

## mkGridInteractive.ipynb

This is the interactive grid generator.  It was
created as a way to generate model grids without
needing to touch the command line or scripts.

## mkGridIterative.ipynb

This script demonstrates how to create a model
grid using the programming language.  The
script also demonstrates loading and displaying
existing model grids.

## mkGridsExample01.py

This script demonstrates creation of a model grid
over California.  It is Lambert Conformal Conic
(LCC) and 20x30.  This also demonstrates a high
level of logging at the DEBUG level and storing
of messages to `LCC_20x30.log`.  This will create
graphical plots of the grid in JPG and PDF formats
(if supported on your system).

For grid creation and plotting, parameters have
been defined.  Most paramters have a default value.
If a parameter is not defined, a warning or
informational message may be emitted indicating
the default value that the library is using.

## mkGridsExample02.py

This script demonstrates some of the logging
and debugging methods integrated into the
gridtools library.

## mkGridsShowLoggers.py

This scripts demonstrates how to access logging
from other python modules should it become
necessary for debugging problems.

## mkGridsExample03.py

This example generates a Mercator grid off
the west coast of California.  A similar
grid is constructed in FRE-NCtools, in
example [03FRE](mkGridsExample03FRE.py),
for comparison.

Please see the
[API](https://mom6gridtools.readthedocs.io/en/latest/guides/index.html)
manual for a guide
that compares gridtools and FRE-NCtools
grid generation methods.

## mkGridsExample03FRE.py

This script generates a Mercator grid using
FRE-NCtools.

To successfully create a topography file, these
things are needed for `make_topog`:
 * Input topography/bathymetry with variable of
   type `NC_DOUBLE`, `NC_FLOAT` or `NC_INT`.
 * Input topography/bathymetry with an attribute
   named `missing_value` with type `NC_DOUBLE`,
   `NC_FLOAT`, `NC_INT`, `NC_SHORT` or `NC_CHAR`.
 * Ocean vertical grid

Please see the
[API](https://mom6gridtools.readthedocs.io/en/latest/guides/index.html)
manual for a guide
that compares gridtools and FRE-NCtools
grid generation methods.

## mkGridsExample04.ipynb

This example demonstrates the manual
reconstruction of the IBCAO grid and
the use of gridtools to construct the
same grid.

## mkGridsExample04a.ipynb

(INCOMPLETE): This example is the same program
from Example 4 except there is an attempt to
use dask.

## mkGridsExample05.py

This example demonstrates the manual
reconstruction of the IBCAO grid and
the use of gridtools to construct the
same grid.

## mkGridsExmaple05a.py

This example is the same as Example 5 except
a slightly different radius of the Earth is
chosen to show how it impacts model grid
creation.

## mkGridsExample06.py

This creates a mini IBCAO grid that will fit
on smaller memory systems.  The plot of the
grid shows the grid cells.

## mkGridsExample07.py

This is currently a full fledged example of
creating a grid, creating a topography,
initial ocean/land masks and FMS coupling
and mosaic files that should allow basic
MOM6 modeling operation.  See the manual
for an expanded description of this
example.

## mkGridsExample07a.ipynb

This example is just Example 7 but in a
jupyter notebook form.

## mkGridsExample08.py

This example exercises the gridtools.regridTopo()
function that provides a bathymetry and ocean
mask that is a fraction instead of 0 and 1 bits.

*NOTE*: This example requires a fair bit of memory
to run.  This example will **NOT** run on a machine
with 8 GB of RAM.

## mkGridsExample09.py

This example requires the use of ipython.  The
interpreter must be launched with pylab:
`ipython --pylab`.  Code copy and pasted into
ipython.

After editing, the function to write out a ROMS
grid does function.

```
In [2]: romsObj.write_ROMS_grid(romsGrd, filename='grid_py.nc')
 ... wrote  theta_s
 ... wrote  theta_b
 ... wrote  Tcline
 ...
```

### matplotlib pylab

The backend must be able to open an interactive
window.  The `agg` backend is not sufficient:

```
$ ipython --pylab
Python 3.8.10 (default, Jun  2 2021, 10:49:15)
Type 'copyright', 'credits' or 'license' for more information
IPython 7.24.0 -- An enhanced Interactive Python. Type '?' for help.
Using matplotlib backend: agg
```

#### aarch64
The python venv does not support installation of pyqt
at the moment.  The module exists, but it fails to
install via `pip`.  The conda package manager does
seem to support ipython pylab:

```
$ ipython --pylab
Python 3.9.4 | packaged by conda-forge | (default, May 10 2021, 22:03:40)
Type 'copyright', 'credits' or 'license' for more information
IPython 7.24.0 -- An enhanced Interactive Python. Type '?' for help.
Using matplotlib backend: Qt5Agg
```

## mkGridsExample09a.ipynb

This example is a jupyter notebook that opens
a ROMS model grid for ocean mask editing.

## mkGridsExample09b.ipynb

This example is a jupyter notebook that opens
a MOM6 model grid for ocean mask editing.

## mkGridsExample10a.ipynb

NOTE: INCOMPLETE EXAMPLE

This example requires the use of
`ipython --pylab`.  The ipython interpreter
should be started and commands from the
script copy and pasted to start the editor.

Once editing is complete, there are more commands
required to save the edited grid.

## NewGridMOM6.ipynb

This is all the code from a fully written tutorial about
constructing a MOM6 model grid.

See: [Build and Edit a MOM6 Grid in Jupyter](https://mom6gridtools.readthedocs.io/en/latest/tutorials/jupyterMOM6.html)

# DIR: ./bokeh

This provides a quick demo of the software package
used to create the interactive ocean mask editor
for jupyter.

## clickablePlot.ipynb

This demonstrates a quick editor using a
simple 1D latitude and longitude grid.

## clickablePlotCurvilinear.ipynb

This demonstrates a an editor using a
a curvilinear grid in a 2D latitude
and longitude grid.  To find the grid
point for each click, a great circle
calculation is required.

NOTE: It may take some time to update
between mouse clicks due to the large
grid.  The implementation of the
ocean mask editor uses a subset of
the grid to increase responsiveness.
