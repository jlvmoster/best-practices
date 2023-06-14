# General Python Best Practices

## Install Pyenv and Poetry as the De Facto Modern Python Environment

Install pyenv by following these [instructions](https://github.com/pyenv/pyenv#installation).

Install poetry after installing the specified Python version with pyenv like so:
```bash
pip install poetry
```

## Check For Outdated Packages

Run the following command to list outdated modules:
```bash
pip list --outdated
```

## Create a Virtual Environment With `venv` [DEPRECATED - USE PYENV INSTEAD]:

<del>

Run `venv` in a directory to create a virtual python environment:
```bash
python -m venv venv
```

Activate the `venv` environment:
```bash
./venv/Scripts/activate
```

Deactive when finished:
```bash
deactivate
```

</del>

## Self Update Pip

Update pip with the `-U` flag which is shorthand notation for `--upgrade`:
```bash
pip install --user -U pip
```
