# Cheatsheet - Terminal

## Environment variables

Set variables in `.env` file or set them through terminal:

```bash
export VARIABLE_NAME="value"
```

Load .env file:

```bash
export $(grep -v '^#' .env)    
```

Test if variable is set:

```bash
echo $VARIABLE_NAME
```

## Pip

Pip install in edit mode:

```bash
pip install -e .
```

## Virtualenv

Setting up virtualenv (create, start, stop):

```bash
virtualenv venv
source venv/bin/activate
deactivate
```

### Using virtualenv with Jupyter Lab

Setting up Jupiter lab:

```bash
pip install jupyterlab
pip install ipykernel
python -m ipykernel install --user --name=venv
```

List and remove virtualenvs from Jupter:

```bash
jupyter kernelspec list
Jupiter kernelspec uninstall venv
```
