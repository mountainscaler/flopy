### Version 3.2.4
* AGU Code Jam

### Version 3.2.3
* Added support for the SEAWAT viscosity (VSC) package.
* Added support for the MODFLOW Stream (STR), Streamflow-Routing (SFR2), Subsidence (SUB), and Subsidence and Aquifer-System Compaction Package for Water-Table Aquifers (SWT) Packages.
* Mt3d model was redesigned based on recent changes to the Modflow model.  Mt3d packages rewritten to support multi-species.  Primary packages can be loaded (btn, adv, dsp, ssm, gcg).  Array utilities modified to read some MT3D RARRAY formats.
* Fixed array loading functionality for case when the CNSTNT value is zero.  If CNSTNT is zero and is used as an array multiplier, it is changed to 1 (as done in MODFLOW).
* Added support for the MODFLOW HYDMOD (HYD) Package and reading binary files created by the HYDMOD Package (`HydmodObs` Class) in the `flopy.utils` submodule.
* `flopy.utils.CellBudgetFile` returns a numpy recarray for list based budget data. Previously a dictionary with the `node` number and `q` were returned. The recarray will return the `node` number, `q`, and the `aux` variables for list based budget data.
* Added travis-ci automated testing.

### Version 3.2.2
* *FloPy<sub>3</sub>* now supports some simple plotting capabilities for two- and three-dimensional model input data array classes  and transient two-dimensional stress period input data using the `.plot()` methods associated with the data array classes (`util_2d`, `util_3d`, and `transient_2d`). The model results reader classes (`HeadFile`, `UcnFile`, and `CellBudgetFile`) have also been extended to include a `.plot()` method that can be used to create simple plots of model output data. See the notebook [flopy3_PlotArrayExample](http://nbviewer.ipython.org/github/modflowpy/flopy/blob/master/examples/Notebooks/flopy3_PlotArrayExample.ipynb).

* Added `.to_shapefile()` method to two- and three-dimensional model input data array classes (`util_2d` and `util_3d`), transient two-dimensional stress period input data classes (`transient_2d`), and model output data classes (`HeadFile`, `UcnFile`, and `CellBudgetFile`) that allows model data to be exported as polygon shapefiles with separate attribute columns for each model layer.

* Added support for ASCII model results files.

* Added support for reading MODPATH version 6 pathline and endpoint output files and plotting MODPATH results using mapping capabilities in `flopy.plot` submodule.

* Added `load()` method for MODFLOW GMG solver.

* Bug fixes:
  1. Multipler in array control record was not being applied to arrays
  2. vani parameter was not supported

### Version 3.2.1
* *FloPy<sub>3</sub>* can now be used with **Python 3.x**

* Revised setters for package class variables stored using the `util_2d` or `util_3d` classes.

* Added option to load a subset of MODFLOW packages in a MODFLOW model name file using `load_only=` keyword.

### Version 3.1
* *FloPy<sub>3</sub>* now supports some simple mapping and cross-section capabilities through the `flopy.plot` submodule. See the notebook [flopy3_MapExample](http://nbviewer.ipython.org/github/modflowpy/flopy/blob/master/examples/Notebooks/flopy3_MapExample.ipynb).

* Full support for all Output Control (OC) options including DDREFERENCE, SAVE IBOUND, and layer lists. All Output Control Input is specified using words. Output Control Input using numeric codes is still available in the ModflowOc88 class. The ModflowOc88 class is currently deprecated and no longer actively maintained.

* Added support for standard MULT package FUNCTION and EXPRESSION functionality are supported. MODFLOW parameters are not supported in `write()` methods. 

### Version 3.0

*FloPy<sub>3</sub>* is significantly different from *FloPy<sub>2</sub>* (previously hosted on [googlecode](https://code.google.com/p/flopy/)). The main changes are:

* *FloPy<sub>3</sub>* is fully zero-based. This means that layers, rows and columns start counting at *zero*. The reason for this is consistency. Arrays are zero-based by default in Python, so it was confusing to have a mix.

* Input for packages that take *layer, row, column, data* input (like the wel or ghb package) has changed and is much more flexible now. See the notebook [flopy3boundaries](http://nbviewer.ipython.org/github/modflowpy/flopy/blob/master/examples/Notebooks/flopy3boundaries.ipynb)

* Input for the MT3DMS Source/Sink Mixing (SSM) Package has been modified to be consistent with the new MODFLOW boundary package input and is more flexible than previous versions of *FloPy*. See the notebook [flopy3ssm](http://nbviewer.ipython.org/github/modflowpy/flopy/blob/master/examples/Notebooks/flopy3_multi-component_SSM.ipynb)

* Support for use of EXTERNAL and OPEN/CLOSE array specifiers has been improved.

* *load()* methods have been developed for all of the standard MODFLOW packages and a few less used packages (*e.g.* SWI2).

* MODFLOW parameter support has been added to the `load()` methods. MULT, PVAL, and ZONE packages are now supported and parameter data are converted to arrays in the `load()` methods. MODFLOW parameters are not supported in `write()` methods.  