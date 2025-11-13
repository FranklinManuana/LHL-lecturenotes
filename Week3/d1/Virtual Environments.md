n this activity, we will practice managing and working with **virtual environments** in conda. Our goal is to get familiar with them and install them in JupyterLab.

Note

If you, at this point, still don't have Anaconda installed, please refer back to the Prep Course where we went through the installation in detail.

### Determining Your Version of Python

Instruction

**Linux and Mac:**

Open your **Terminal** and start Python using the command `python`.

**Windows:**

Use **Anaconda Prompt** and start Python using the command `python`.

You should see something similar to this:

![](https://i.imgur.com/CamRNN5.png)

Take a moment to note the version of Python you are running and then be sure to switch back to the terminal.

Note

When running Python in the Terminal we can exit it by typing either `exit()` or `quit()` commands.

### Find out what is Inside PATH

When executing the command `python`, your command line goes through your computer and looks for the executable file. The environmental variable `PATH` specifies where to look for commands.

Instruction

Check the content of your variable `PATH`

**Linux and Mac:**

```shell
echo $PATH
```

**Windows:**

```shell
echo %PATH%
```

You should see similar results to those in the image below with `..../anaconda3/bin` for Linux and Mac or `...\anaconda3\Library\bin;` for Windows.

![](https://i.imgur.com/kWANABK.png)

This allows the command line to use all Conda commands. When you execute any command in the command line it searches for the executable in the following locations:

- the current directory (i.e. the directory where we are at that time)
- other directories that are specified in the variable `$PATH`.

This is true for any operating system.

Now, let's see what happens when we create a virtual environment.

### Creating a Virtual Environment

Instruction

Create a virtual environment using `conda` command inside the terminal. The following command will create the virtual environment called `test_env` with **python 3.9** installed:

```shell
conda create -n test_env python=3.9
```

The environment can be activated by the command below in both, Terminal and Anaconda Prompt.

```shell
conda activate test_env
```

Instruction

Now, start your Python again using the command `python`. Do you see something different?

A different Python, the one in the new virtual environment, is launched.

![](https://i.imgur.com/48OV5Ie.png)

When we check the content of the variable `PATH` we can see why a different Python was launched:

![](https://i.imgur.com/nEsrdUJ.png)

When we activate the new environment, the `PATH` variable is added to the beginning of the existing directories. This allows the new virtual environment to point to the Python we are specifying.

### Adding the Environment to Jupyter

In Mac and Linux, JupyterLab has to be run from the default environment.

![](https://i.imgur.com/QxLPEjh.png)

In Windows, it can be launched from the new `test_env` as well but the version of Python in the notebooks will be the default one.

So the question is, how can we work with different Pythons inside the Jupyter notebook?

Instruction

Follow the instructions in the PDF copy of this Medium article [How to add your Conda environment to your Jupyter notebook in just 4 steps](https://drive.google.com/file/d/1JW7UWy0jVtTfd626CkW3SalQpEy9BZTO/view?usp=drive_link) to activate the new environment inside Jupyter. Don't forget to change the parameter **name** (--name) to `test_env`. You can follow these instructions in both, _Terminal_ and _Anaconda Prompt_.

Instruction

Go back to your `base` environment and start JupyterLab:

```shell
conda deactivate
jupyter lab
```

Once it starts, you should see the new kernel there:

![](https://i.imgur.com/Wg4zb6g.png)

Open the new notebook using the kernel and type in the first cell:

```python
import sys
sys.executable
```

The command will print the location of the Python it is running. It should be the same as the one in `PATH` when the environment was activated.