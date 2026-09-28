# Adnan Ali Syed - Quarto Portfolio

This repository contains my personal website and computational blog posts created using Quarto. The website includes analyses written in both Python and R.

## Requirements

The website was built using:

- Quarto: `<YOUR QUARTO VERSION>`
- uv: `<YOUR UV VERSION>`
- Python: `3.14`
- R: `<YOUR R VERSION>`

Python dependencies are managed using `uv`, while R dependencies are managed using `renv`.

## Build the website from a fresh clone

Clone the repository:

```bash
git clone https://github.com/adnan-ali-syed/adnan-ali-syed.github.io.git
cd adnan-ali-syed.github.io
```

Restore the Python environment:

```bash
uv sync
```

Restore the R environment:

```bash
R -e 'renv::restore()'
```

Render the complete Quarto website:

```bash
uv run quarto render
```

The generated website will be written to:

```text
docs/
```

The generated home page is:

```text
docs/index.html
```

To open the generated site locally on macOS:

```bash
open docs/index.html
```

Alternatively, open `docs/index.html` manually in a web browser.

## Data

The Python and R computational posts use the Palmer Penguins dataset:

https://allisonhorst.github.io/palmerpenguins/

The dataset is provided through the `palmerpenguins` packages for Python and R, so no separate data file needs to be downloaded during rendering.

An internet connection is required when initially restoring the Python and R package environments. Once the required packages are installed, the analyses use the dataset bundled with the packages.