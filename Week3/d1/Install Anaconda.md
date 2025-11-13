In this activity, we are going to install the Anaconda distribution on our computer.

Note

If you have a Mac with Apple Silicon (M1), please follow the instructions at the bottom is this activity.

Note

Before we let you jump into action for installing Anaconda, we **do** recommend adding Anaconda to your PATH environment variable during installation (for Windows, they say they don't recommend it). This helps us to run different Anaconda commands from our command line.

Feel free to change the install directory to your preferred location.

Instruction

You're now ready! Install Anaconda (Version 3.9): [**installation package**](https://www.anaconda.com/download) (for Anaconda).

Once everything is installed, open the terminal (there's an Anaconda prompt in case you are on Windows) on your machine and try the command `conda`. For different options how you can verify your installation, follow [**this link**](https://docs.anaconda.com/anaconda/install/verify-install/) from the official documentation.

In case you get the `command not found` error, follow [**this thread**](https://stackoverflow.com/questions/18675907/how-to-run-conda) to solve it. However, it should be done automatically by the Anaconda installer.

## Installation of Anaconda for Apple Silicon

Instead of installing Anaconda through its website, we will use homebrew and miniforge to achieve the same result. Those instructions assume that you have homebrew installed on your computer.

- Install miniforge : `brew install miniforge`
- Quit & Reopen the terminal
- Create an environment : `conda create --name base_env python=3.8`
- Link the environment to ZSH : `conda init zsh`
- Quit & Reopen the terminal
- Activate the environment : `conda activate base_env`

Each time we will want to use this environment, we need to activate the proper environment by typing `conda activate base_env`.