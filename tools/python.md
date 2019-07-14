# pipenv

### packagind, dependencies and venv management

Install `pipenv`

    pip install --user pipenv

> On Linux and macOS you can find the user base binary directory by running `python -m site --user-base` and adding bin to the end. For example, this will typically print `~/.local` (with `~` expanded to the absolute path to your home directory) so you’ll need to add `~/.local/bin` to your `PATH`. You can set your `PATH` permanently by modifying `~/.profile`.

Install dependencies:

    cd myproject
    pipenv install requests

Start python:

    pipenv run python main.py

Remove `venv`

    pipenv --rm
