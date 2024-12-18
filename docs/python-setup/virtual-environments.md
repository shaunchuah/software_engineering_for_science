# Virtual Environments

## The Concept of Virtual Environments

Virtual environments are a way to create isolated Python environments for your projects. This is useful when you have multiple projects that require different versions of Python or different packages. Virtual environments are also useful when you want to avoid installing packages globally on your system.

For example, you may have one project that requires Pandas version 1.3.0 and another project that requires Pandas version 1.2.0. By creating separate virtual environments for each project, you can install the required version of Pandas in each environment without affecting the other project.

## My Approach to Virtual Environments

By default, I name my virtual environment `venv` and keep it within the project directory. I add the `venv` directory to the `.gitignore` file to avoid committing it to version control.

Each project I work on has its own virtual environment, which helps me manage dependencies and avoid conflicts between projects. One benefit of keeping the virtual environment within your project directory is that VSCode can detect it and automatically activate it when you open the project.

## Creating a Virtual Environment

To create a virtual environment, you can use the `venv` module that comes with Python. Open a terminal window **within the project directory** and run the following command to create a new virtual environment named `venv`:

```bash
python3 -m venv venv
```

This command creates a new directory named `venv` in your current working directory. Inside this directory, a new Python environment is created with its own copy of the Python interpreter and standard library.

## Activating a Virtual Environment

To activate the virtual environment, run the following command in your terminal:

=== "macOS/Linux"
    ```bash
    source venv/bin/activate
    ```
=== "Windows"
    ```bash
    venv\Scripts\activate
    ```

When the virtual environment is activated, your terminal prompt will change to show the name of the virtual environment. For example, `(venv) $`.

## Deactivating a Virtual Environment

To deactivate the virtual environment and return to the global Python environment, run the following command:

=== "macOS/Linux/Windows"
    ```bash
    deactivate
    ```

## Next Steps

Now that you are familiar with this concept, we can now move on to learn how to install python packages.
