# Adnan Ali Syed - Quarto Portfolio

This repository contains my personal website built with Quarto. It includes regular blog content as well as two reproducible computational posts: a Python analysis of the Palmer Penguins dataset and an R analysis of the Gapminder dataset.

## Software requirements

The project was built using:

- **Quarto:** 1.10.18
- **uv:** 0.12.5
- **Python:** 3.14
- **R:** 4.6.1

Python dependencies are managed with `uv` using `pyproject.toml` and `uv.lock`.  
R dependencies are managed with `renv` using `renv.lock`.

You do **not** need to install `renv` manually before restoring the project. The repository contains `.Rprofile` and `renv/activate.R`, which allow `renv` to bootstrap itself when R starts.

Before building the site, make sure that Git, Quarto, `uv`, and R are installed and available from the command line.

## Reproducing the website from a fresh clone

All of the commands below should be run from a terminal.

### 1. Clone the repository

```bash
git clone https://github.com/adnan-ali-syed/adnan-ali-syed.github.io.git
cd adnan-ali-syed.github.io
```

After the `cd` command, the remaining commands should be run from the **top level of the repository**, where `_quarto.yml`, `pyproject.toml`, and `renv.lock` are located.

### 2. Restore the Python environment

```bash
uv sync
```

The project pins Python 3.14 in `.python-version`. `uv` uses `pyproject.toml` and `uv.lock` to recreate the Python environment in `.venv`.

### 3. Restore the R environment

```bash
R -e 'renv::restore()'
```

This restores the R packages recorded in `renv.lock`. If R asks for confirmation while restoring packages, confirm the installation.

### 4. Render the complete Quarto website

```bash
uv run quarto render
```

Running Quarto through `uv` ensures that the Python computational post uses the Python environment created for this project. The command should be run from the repository root so that the R project also finds `.Rprofile` and activates the `renv` environment.

## Build output

The Quarto project is configured in `_quarto.yml` to write the rendered website to:

```text
docs/
```

The rendered home page is:

```text
docs/index.html
```

On macOS, the built site can be opened locally with:

```bash
open docs/index.html
```

On another operating system, open `docs/index.html` in a web browser.

The published version of the site is available at:

https://adnan-ali-syed.github.io

## Data used in the computational posts

### Python post: Palmer Penguins

The Python post uses the **Palmer Penguins** dataset:

https://allisonhorst.github.io/palmerpenguins/

The dataset is accessed through the Python `palmerpenguins` package. It is bundled with the package, so the render does not download a separate data file.

### R post: Gapminder

The R post uses the **Gapminder** dataset:

https://www.gapminder.org/data/

The dataset is accessed through the R `gapminder` package. It is bundled with the package, so the render does not download a separate data file.

## Network requirements

A network connection is required the first time the project is reproduced so that:

- `uv sync` can restore the Python packages recorded in `uv.lock`;
- `renv` can bootstrap itself if necessary;
- `renv::restore()` can restore the R packages recorded in `renv.lock`; and
- `uv` can obtain a compatible Python 3.14 installation if one is not already available.

After the required environments have been restored, the computational posts use datasets provided by their installed packages and do not need to fetch the datasets separately from the web.
