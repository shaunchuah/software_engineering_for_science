# Installing Python Packages

Python packages are collections of modules that provide additional functionality to your Python programs. You can install Python packages using the `pip` package manager, which comes pre-installed with Python. On MacOS, you may need to use `pip3` instead of `pip`.

Before installing packages, make sure your virtual environment is activated. If your virtual environment is not activated, the packages will be installed globally on your system and this can create conflicts between different projects.

```bash
pip install package_name
```

Replace `package_name` with the name of the package you want to install. You can also specify the version of the package you want to install by adding `==version_number` after the package name.

For example, to install the `numpy` package, you can run:

```bash
pip install numpy
```

## Managing Dependencies With `requirements.txt`

It is a convention of python projects to have a `requirements.txt` file that lists all the dependencies of the project. This file can be used to install all the dependencies at once using the following command:

```bash
pip install -r requirements.txt
```

To generate a `requirements.txt` file, you can use the following command:

```bash
pip freeze > requirements.txt
```

This command will create a `requirements.txt` file in the current directory with a list of all the packages installed in the current environment.

## My Approach

I prefer to manage `requirements.txt` by hand, only specifying the essential packages for that project. This is because most packages will have their own individual dependencies. `pip` will install these dependencies automatically when you install the package and try and resolve any conflicts. If the pinned requirements are too strict, you may run into issues when trying to install things if you upgrade a package for instance.

For example:

```plaintext title="requirements.txt"
numpy==2.0.2
requests==2.32.3
pandas==2.2.3
seaborn==0.13.2
```

Pinning your dependencies is a good practice to ensure that your project is reproducible in the future. If you are working on a team project, it is important to have a `requirements.txt` file to ensure that everyone is using the same versions of the packages.

This is one method of managing dependencies for Python projects. We will cover a more advanced method known as containerization later on. If you are just starting your coding journey, I would start off with this technique for now and as you gain more experience, you may wish to explore containerization later on.

There is a learning curve for this (you need to be familiar with Linux, package managers, and how software is installed generally speaking) and we will build incrementally on your knowledge as we progress through the course.
