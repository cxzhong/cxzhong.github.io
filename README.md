# Chenxin Zhong's Academic Pages

**Personal and professional portfolio website for Chenxin Zhong, showcasing research in mathematics and cryptography.**

![Academic Pages template example](images/homepage.png "Academic Pages template example")

## Featured Project: BLASter

This repository includes research and implementation of **BLASter**, a proof-of-concept LLL-like lattice reduction algorithm that incorporates several performance optimizations:

- **Parallelization** for improved computational efficiency
- **Segmentation** for better memory management  
- **Seysen's reduction** instead of traditional size reduction
- **Linear algebra library integration** for optimized operations

### BLASter Overview

BLASter demonstrates significant speed improvements in lattice reduction, which is fundamental to cryptographic applications including:
- Post-quantum cryptography
- Lattice-based encryption schemes
- Cryptanalysis of lattice-based problems

**Key Features:**
- Parallel processing capabilities
- Progressive BKZ reduction with configurable parameters
- Deep-LLL reduction with adjustable depth
- Support for q-ary lattice generation

**Performance Example:**
```bash
time latticegen q 128 64 20 p | src/app.py -pq
# Expected: Root Hermite factor: 1.020447, ∥b_1∥ = 11906.636
# Runtime: ~0.754s real time, ~2.271s user time
```

*Note: This is research software focused on demonstrating algorithmic improvements in lattice reduction.*

# Getting Started

This website serves as a portfolio for cryptographic research, with a focus on lattice reduction algorithms and their applications.

## BLASter Requirements

For running the BLASter lattice reduction implementation:

- **Python 3** with Cython 3.0 or later
- **Required Python modules:** `cysignals numpy setuptools`
- **Eigen library** version 3 or later
- **Optional:** `virtualenv` for local development, `fplll` for lattice generation

## BLASter Setup

1. **Install dependencies:**
   ```bash
   make eigen3    # Install Eigen library locally
   make venv      # Create virtual environment (optional)
   make          # Compile Cython files
   ```

2. **Run examples:**
   ```bash
   # Basic lattice reduction
   time latticegen q 128 64 20 p | src/app.py -pq
   
   # Deep-LLL with depth 4
   src/app.py -pq -i {lattice} -d4
   
   # Progressive BKZ-60 with 1 tour
   src/app.py -pq -i {lattice} -b60 -t1 -P2
   ```

## Website Development

For modifying this academic website:

1. Set site-wide configuration and add your content
2. Upload files (PDFs, etc.) to the `files/` directory  
3. Use Jupyter notebooks in `markdown_generator/` for publications and talks
4. Check deployment status in repository settings under "GitHub pages"

See more info at https://academicpages.github.io/

## Running locally

When you are initially working on your website, it is very useful to be able to preview the changes locally before pushing them to GitHub. To work locally you will need to:

1. Clone the repository and made updates as detailed above.

### Using a different IDE
1. Make sure you have ruby-dev, bundler, and nodejs installed
    
    On most Linux distribution and [Windows Subsystem Linux](https://learn.microsoft.com/en-us/windows/wsl/about) the command is:
    ```bash
    sudo apt install ruby-dev ruby-bundler nodejs
    ```
    If you see error `Unable to locate package ruby-bundler`, `Unable to locate package nodejs `, run the following:
    ```bash
    sudo apt update && sudo apt upgrade -y
    ```
    then try run `sudo apt install ruby-dev ruby-bundler nodejs` again.

    On MacOS the commands are:
    ```bash
    brew install ruby
    brew install node
    gem install bundler
    ```
1. Run `bundle install` to install ruby dependencies. If you get errors, delete Gemfile.lock and try again.

    If you see file permission error like `Fetching bundler-2.6.3.gem ERROR:  While executing gem (Gem::FilePermissionError) You don't have write permissions for the /var/lib/gems/3.2.0 directory.` or `Bundler::PermissionError: There was an error while trying to write to /usr/local/bin.`
    Install Gems Locally (Recommended):
    ```bash
    bundle config set --local path 'vendor/bundle'
    ```
    then try run `bundle install` again. If succeeded, you should see a folder called `vendor` and `.bundle`.

1. Run `jekyll serve -l -H localhost` to generate the HTML and serve it from `localhost:4000` the local server will automatically rebuild and refresh the pages on change.
    You may also try `bundle exec jekyll serve -l -H localhost` to ensure jekyll to use specific dependencies on your own local machine.

If you are running on Linux it may be necessary to install some additional dependencies prior to being able to run locally: `sudo apt install build-essential gcc make`

## Using Docker

Working from a different OS, or just want to avoid installing dependencies? You can use the provided `Dockerfile` to build a container that will run the site for you if you have [Docker](https://www.docker.com/) installed.

You can build and execute the container by running the following command in the repository:

```bash
chmod -R 777 .
docker compose up
```

You should now be able to access the website from `localhost:4000`.

### Using the DevContainer in VS Code

If you are using [Visual Studio Code](https://code.visualstudio.com/) you can use the [Dev Container](https://code.visualstudio.com/docs/devcontainers/containers) that comes with this Repository. Normally VS Code detects that a development coontainer configuration is available and asks you if you want to use the container. If this doesn't happen you can manually start the container by **F1->DevContainer: Reopen in Container**. This restarts your VS Code in the container and automatically hosts your academic page locally on http://localhost:4000. All changes will be updated live to that page after a few seconds.

# Research Focus

This portfolio showcases work in **lattice-based cryptography** and **algorithmic optimization**. The BLASter project demonstrates how classical lattice reduction algorithms can be enhanced through:

- Modern parallel computing techniques
- Advanced mathematical optimizations  
- Practical implementation considerations for cryptographic applications

The research contributes to the broader cryptographic community's understanding of lattice reduction efficiency, which is crucial for both constructive and analytical applications in post-quantum cryptography.

## Disclaimer

BLASter is a **proof of concept** focused on demonstrating algorithmic improvements. It is not intended for production use and:

- Does not guarantee algorithm termination or correctness on all lattices
- Does not support lattices with large entries  
- Is not actively maintained for robustness or efficiency improvements

However, questions about design choices ("Why is X done in Y way?") are welcomed, and the cryptographic community is encouraged to build upon these ideas for robust implementations.

# Maintenance

Bug reports and feature requests to the template should be [submitted via GitHub](https://github.com/academicpages/academicpages.github.io/issues/new/choose). For questions concerning how to style the template, please feel free to start a [new discussion on GitHub](https://github.com/academicpages/academicpages.github.io/discussions).

This repository was forked (then detached) by [Stuart Geiger](https://github.com/staeiou) from the [Minimal Mistakes Jekyll Theme](https://mmistakes.github.io/minimal-mistakes/), which is © 2016 Michael Rose and released under the MIT License (see LICENSE.md). It is currently being maintained by [Robert Zupko](https://github.com/rjzupkoii) and additional maintainers would be welcomed.

## Bugfixes and enhancements

If you have bugfixes and enhancements that you would like to submit as a pull request, you will need to [fork](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/working-with-forks/fork-a-repo) this repository as opposed to using it as a template. This will also allow you to [synchronize your copy](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/working-with-forks/syncing-a-fork) of template to your fork as well.

Unfortunately, one logistical issue with a template theme like Academic Pages that makes it a little tricky to get bug fixes and updates to the core theme. If you use this template and customize it, you will probably get merge conflicts if you attempt to synchronize. If you want to save your various .yml configuration files and markdown files, you can delete the repository and fork it again. Or you can manually patch.

---
<div align="center">
    
![pages-build-deployment](https://github.com/academicpages/academicpages.github.io/actions/workflows/pages/pages-build-deployment/badge.svg)
[![GitHub contributors](https://img.shields.io/github/contributors/academicpages/academicpages.github.io.svg)](https://github.com/academicpages/academicpages.github.io/graphs/contributors)
[![GitHub release](https://img.shields.io/github/v/release/academicpages/academicpages.github.io)](https://github.com/academicpages/academicpages.github.io/releases/latest)
[![GitHub license](https://img.shields.io/github/license/academicpages/academicpages.github.io?color=blue)](https://github.com/academicpages/academicpages.github.io/blob/master/LICENSE)

[![GitHub stars](https://img.shields.io/github/stars/academicpages/academicpages.github.io)](https://github.com/academicpages/academicpages.github.io)
[![GitHub forks](https://img.shields.io/github/forks/academicpages/academicpages.github.io)](https://github.com/academicpages/academicpages.github.io/fork)
</div>
