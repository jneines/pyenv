# pyenv
A bash script to create miniconda3 based Python environments from scratch

`pyenv` can be used to create miniconda3 based python environments without having Python installed beforehand. It is tested to work on Linux and MacOS on x86_64 machines.

You can call pyenv like this:

    ./pyenv ENVIRONMENT_NAME APPLICATION [PACKAGE [PACKAGE ...]]

where `ENVIRONMENT_NAME` is the name for the environment to use and `APPLICATION` is an identifier for the application to start within the desired environment. See below for more details on the application identifiers.

##### ENVIRONMENT_NAME

The environment name consists of two parts separated by a single dash. The first is a free to choose single word identifier, such as *test*. The second part describes the Python version to be used starting with the two letters *py* and a number of further digits to specify the exact version of the Python interpreter to be used. For example *py36* would choose a Python version 3.6 interpreter for the environment. As a result a complete example for a valid environment identifier would be *test-py36* in this case.

##### APPLICATION

The next parameter identifies the application to start in the environment. Currently the following identifiers are understood.

Use 

`jn` - to start a jupyter notebook and open its web page in your default browser, like it is the default bahaviour.

`jnnb` - to start a jupyter notebook without opening the web page. This is handy for remote locations.

`python` - start the plain interpreter within the environment.

`ipython` - start the text based IPython interpreter.

`bash` - to start a bash shell in the environment. This is useful to update the environment or add packages.

`update` - to trigger a `conda update --all` updating your environment to the latest versions of all packages.

`remove` - to completely delete the environment.

##### adding further packages

The optional list of following arguments are considered to be packages that should directy be installed with creating or entering the environment.


##### workflow

`pyenv` will initially check if a miniconda installation is available in its default location, which is set to be a folder based on your user name in `/tmp`. This has been chosen to not interact with any existing miniconda3 installations. However this behaviour can be adjusted.

If no miniconda3 installation is available yet the corresponding installer will be downloaded and executed to ensure the necessary setup.

Afterwards the existence of the specified environment will be checked. Should it not exist it will be created depending on the settings in the label itself. See above for details. If additional packages are specified on the command line they will be installed as well.

As a final step the environment is entered and the application defined by its corresponding label is executed. This is, in contrast to the default behaviour in miniconda3, not performed by activating the environment, but by configuring and executing a new subshell for the command. On exiting the application the subshell will quit as well, leaving your shell in its prior state. With using this scheme no activate or deactivate calls are necessary.

##### adjusting to local needs

`pyenv` can be adjusted to respect special settings suiting your needs. Currently this can be done by creating a file called `local.conf` stored next to `pyenv`, which is sourced by `pyenv` on each execution. In this file almost all environment variables can be adjusted. This is especially useful if you would like to add additional channels or replace the defaults with your mirrored ones to accelerate repeated installations.



```python

```
