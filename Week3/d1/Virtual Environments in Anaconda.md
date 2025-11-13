### Why Do We Use A Virtual Environment?

Nearly everyone in the Python community suggests that you use virtual environments for all your projects. But why?

The short answer is that Python isn’t great at dependency management. If you’re not specific, then pip will place all the external packages that you install in a folder called site-packages/ in your base Python installation.

One of the reasons why you need a virtual environment is that Linux and macOS come preinstalled with a version of Python that the operating system uses for internal tasks. If you install packages to your operating system’s global Python, these packages will mix with the system-relevant packages. This mix-up could have unexpected side effects on tasks crucial to your operating system’s normal behaviour.

Another reason why you need a virtual environment is that you will often work on different projects. One of your projects might require a different version of an external library than another one. If you have only one place to install packages, then you can’t work with two different versions of the same library.

### Benefits of Using Virtual Environments

The benefits of virtual environments are:

- Virtual environments give you the ability to have multiple environments so that you can have multiple sets of packages for different projects.
- Virtual environments allow you to release your project with its own dependent modules. Thus you can make it easy to create your requirements.txt file.
- Virtual environments allow you to collaborate with others easily. Having everybody’s code in the same environment ensures that the code will run smoothly.

Instruction

Read about the importance of _virtual environments_ [**in this Stack Overflow thread**](https://stackoverflow.com/questions/23948317/why-is-virtualenv-necessary).

Warning

"Virtualenv" can refer both to slang for "virtual environments" and to a Python tool to create isolated environments called **Virtualenv**. Even though the thread mentioned both of them, the goal was to highlight the benefits of "virtualenvs" which apply to both meanings. The great thing about the Anaconda distribution of Python is that it helps us to manage _"virtualenvs"_ without needing any other tool like _Virtualenv_.

Instruction

You will find everything important about managing Anaconda environments in the article: [**Why you need Python environments and how to manage them with Conda**](https://protostar.space/why-you-need-python-environments-and-how-to-manage-them-with-conda) - below the **Summary** of this reading, there is a section about Docker which you can **skip**.

## Conclusion

Being able to set up and work with virtual environments will be an important skill to have as you begin to work on multiple projects with varying requirements. As you work through the activities that require you to set up and use a virtual environment be sure to take the time to understand the process so that you can learn to use them efficiently throughout this course and later in your professional work.