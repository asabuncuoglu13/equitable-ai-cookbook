# Equitable AI Cookbook

A series of essays and experiments to accelerate the equitable AI development. This repository contains code, data, and materials that are part of an ongoing research project. Please note that the work is in a research preview stage and may produce incomplete or inconsistent results. It also contains some content in "under-development" or "in-review" stages. Use at your own discretion, and feel free to contribute or report any issues.

## Usage

### Building the book

If you'd like to develop and/or build the Equitable AI Cookbook book, you should:

1. Clone this repository
2. Run `pip install -r requirements.txt` (it is recommended you do this within a virtual environment)
3. (Optional) Edit the books source files located in the `docs/` directory
4. Run `jupyter-book clean docs/` to remove any existing builds
5. Run `jupyter-book build docs/`

A fully-rendered HTML version of the book will be built in `docs/_build/html/`.

### Hosting the book

Please see the [Jupyter Book documentation](https://jupyterbook.org/publish/web.html) to discover options for deploying a book online using services such as GitHub, GitLab, or Netlify.

For GitHub and GitLab deployment specifically, the [cookiecutter-jupyter-book](https://github.com/executablebooks/cookiecutter-jupyter-book) includes templates for, and information about, optional continuous integration (CI) workflow files to help easily and automatically deploy books online with GitHub or GitLab. For example, if you chose `github` for the `include_ci` cookiecutter option, your book template was created with a GitHub actions workflow file that, once pushed to GitHub, automatically renders and pushes your book to the `gh-pages` branch of your repo and hosts it on GitHub Pages when a push or pull request is made to the main branch.

## Contributors

We welcome and recognize all contributions. You can see a list of current contributors in the [contributors tab](https://github.com/asabuncuoglu13/docs/graphs/contributors).

## Credits

This project is created using the excellent open source [Jupyter Book project](https://jupyterbook.org/) and the [executablebooks/cookiecutter-jupyter-book template](https://github.com/executablebooks/cookiecutter-jupyter-book).


## Planned Next Steps

- [ ] A complete peer-review
- [ ] A detailed data quality review process in "equitable AI" context
- [ ] Red teaming chapter (which will be added when we conduct the event)

## Wish List

- [ ] Offering learning paths with a level of personalisation (regulators, researchers, developers, etc.):
  - [ ] A complete technical AI governance pathway with code, examples and a comparative analysis across countries
  - [ ] A complete equitable/trustworthy AI assurance pathway