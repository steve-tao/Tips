# Recommendation on the layout of a Python project

## A library package
The modern recommendation for the library project layout is the separation
between the porject code and the tests code.  The common practice is to use
the `src` directory for the library code and the `tests` directory for the
test code [[1](https://blog.ionelmc.ro/2014/05/25/python-packaging/)].

Setting the project layout in this manner has many advantages as described in
[[1](https://blog.ionelmc.ro/2014/05/25/python-packaging/)].  We summarize
some of the benefits below.
1. It forces us to test the installed code (similar to the one users is going
   to have) instead of the current working code.
2. It hellps us avoiding the messy editable installs.
3. It allows us the simpler `setup.py` and `MANIFEST` files.

More detailed benefits are described in
[[1](https://blog.ionelmc.ro/2014/05/25/python-packaging/)] and
[[2](https://hynek.me/articles/testing-packaging/)].

### Setting up

#### 1. Prepare the directory

```
setup.py            # The setuptools Python package metadata
LICENSE             # The license file for this module
README.md           # The readme file
pylintrc            # The pylint configuration file
docs/
    userguide.md
    devguide.md
    ...
src/
    appmodule.py
    conftest.py     # Make pytest recognizing the application modules
    module1/
        __init__.py
        part1.py
        part2.py
    ...
tests/
    test_appmodule.py
    module1/
        test_part1.py
        test_part2.py
    ...
```

#### 2. Prepare the `setup.py`

In order for `setup.py` to work properly, add a `where` argument to
`find_packages()` in `setup.py`.

```Python
setup(
    [...]
    packages=find_packages(where="src"),
    package_dir={"": "src"},
)
```

#### 3. (Optional) Add a `conftest.py` into the `src` directory.

This step is unnecessary if we only use `tox` to execute `pytest`.  However, if
we want to also execute `pytest` without running `tox`, we need to make pytest
recognize the `src` directory which can be done by adding an empty file
`conftest.py` into the `src` directory.  With the file `conftest.py`, pytest
will in the background modify the sys.path to include all submodules that are
found under the `src` path [[4](https://stackoverflow.com/questions/34466027/in-pytest-what-is-the-use-of-conftest-py-files)].


#### 4. (Optional) Using Visual Studio Code, make the pylint recognize the `src` directory.

If we use Visual Studio Code and want to use `pylint` to check all the files
under the `src` directory, we need to add the following configuration to the
file `pylintrc` located in the root of the project directory.

```ini
[Master]
init-hook='import sys; sys.path = ["./src"] + sys.path'
```

## References
1. Ionel Cristian Mărieș. 2019. Packaging a python library. idonel’s codelog.
    Retrieved February 12, 2021 from
    https://blog.ionelmc.ro/2014/05/25/python-packaging/.

2. Hynek Schlawack. 2021. Testing & Packaging. Retrieved February 12, 2021 from
    https://hynek.me/articles/testing-packaging/

3. Pytest. 2020. Good Integration Practies. Retrieved February 12, 2021 from
    https://docs.pytest.org/en/stable/goodpractices.html

4. Simone Zandara. 2015. In pytest, what is the use of conftest.py files?
    stackoverflow. Retrieved February 12, 2021 from
    https://stackoverflow.com/questions/34466027/in-pytest-what-is-the-use-of-conftest-py-files
