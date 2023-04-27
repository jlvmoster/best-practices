# General Python Best Practices

## Create a Virtual Environment With `venv`:

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

## Self Update Pip

Update pip with the `-U` flag which is shorthand notation for `--upgrade`:
```bash
python -m pip install -U pip
```
