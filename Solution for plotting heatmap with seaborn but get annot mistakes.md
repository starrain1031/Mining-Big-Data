### Seaborn and Matplotlib have compatibility issues

Because seaborn drawing requires calling matplotlib's API, matplotlib has made some changes to the API after version 3.8.0, which may have caused the call to fail. When the call fails, even if `annot=True` is set, it is not possible to display values within cells when drawing a heatmap.

The current solution is for matplotlib to use version 3.7.3 (which requires installation with pip as Conda only provides version 3.7.2), and seaborne to use the latest version 0.13.2, which is compatible.
PS: Use `pip show seaborn` and `pip show matplotlib` to check the version of both libraries.
