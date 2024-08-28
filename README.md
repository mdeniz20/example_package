Creating a pip-installable package involves several steps, from setting up your project structure to publishing it on PyPI. Here’s a step-by-step guide to help you through the process:

### 0. Registrar to PyPI
Registrar to PyPI with this url [https://pypi.org/](https://pypi.org/).
Set your account and get your token key.
> This token key will be used to upload your package.

You can use the token directly by pasting to inline commend when the upload phase happens, or you can store the key in `~/.pypirc` file in this format:

```
[pypi]
  username = __token__
  password = your-exact_token_key
```
Make sure you only replace ***your-exact\_token\_key*** parameter.

After that step, you will be registered automatically.

### 1. Set Up Your Project Structure

Organize your project files in a standard layout. Here's a basic structure:

```
my_package/
│
├── my_package/
│   ├── __init__.py
│   └── module.py
│
├── tests/
│   ├── __init__.py
│   └── test_module.py
│
├── setup.py
├── README.md
├── LICENSE
└── .gitignore
```

- **`my_package/`**: Your main package directory.
- **`__init__.py`**: This file makes Python treat the directory as a package.
- **`module.py`**: Your Python code.
- **`tests/`**: Directory for test files.
- **`setup.py`**: The script for installing your package.
- **`README.md`**: A file with information about your package.
- **`LICENSE`**: The license for your package.
- **`.gitignore`**: Optional, to exclude files from version control.

### 2. Create the `setup.py` File

The `setup.py` file is crucial for defining your package’s metadata and dependencies. Here's a basic example:

```python
from setuptools import setup, find_packages

setup(
    name='my_package',
    version='0.1.0',
    description='A brief description of the package',
    long_description=open('README.md').read(),
    long_description_content_type='text/markdown',
    author='Your Name',
    author_email='your.email@example.com',
    url='https://github.com/yourusername/my_package',
    packages=find_packages(),
    install_requires=[
        # List your package dependencies here
    ],
    classifiers=[
        'Programming Language :: Python :: 3',
        'License :: OSI Approved :: MIT License',
        'Operating System :: OS Independent',
    ],
    python_requires='>=3.6',
)
```

- **`name`**: The name of your package.
- **`version`**: The initial release version.
- **`description`**: A short summary of your package.
- **`long_description`**: A detailed description, usually from the README file.
- **`author`** and **`author_email`**: Your contact details.
- **`url`**: URL for the project (e.g., a GitHub repository).
- **`packages`**: Automatically finds all packages in the directory.
- **`install_requires`**: List any dependencies your package needs.
- **`classifiers`**: Provide metadata for PyPI.
- **`python_requires`**: Specify the minimum Python version required.

### 3. Create a README File

Write a `README.md` file with information about your package, including installation instructions, usage, and examples.

### 4. Add a License File

Choose a license for your package and add it to the `LICENSE` file. Common choices include MIT, Apache 2.0, or GPL.

### 5. Create a Distribution Package

To make your package installable, you need to create a distribution. First, ensure you have `setuptools` and `wheel` installed:

```bash
pip install setuptools wheel
```

Then, run the following command in your package directory:

```bash
python setup.py sdist bdist_wheel
```

This creates distribution archives in the `dist/` directory.

### 6. Test Your Package Locally

Before publishing, test your package locally using pip:

```bash
pip install .
```

This installs your package from the current directory.

### 7. Publish Your Package to PyPI

To publish your package, you need to use `twine`. First, install it:

```bash
pip install twine
```

Then, upload your package:

```bash
twine upload dist/*
```

You’ll be prompted for your PyPI credentials. If you don’t have an account, you’ll need to create one on [PyPI](https://pypi.org/).

### 8. Update Your Package

When you make changes and want to release a new version, update the version number in `setup.py`, create a new distribution, and upload it to PyPI following the same steps.

That’s it! Your package is now available for others to install using `pip install my_package`.

###Check the [*update_quide*](./update.md) to see how to update your package once you uploaded
