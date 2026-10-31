# Fix an installation problem | FreeMoCap

Skip to main content

This is documentation for FreeMoCap 1.x (legacy), which is no longer actively maintained.

For up-to-date documentation, see the latest version (2.0 (alpha)).

Version: 1.x (legacy)

Human-checked documentationchecked against source

This page is adapted from real, human-written FreeMoCap documentation. If you spot something wrong, please open an issue or use the Edit this page link below to submit a fix.

2026-08-19

v1 (ported, not yet re-checked against v2)

More about how these docs are written

# Fix an installation problem

We have instructions on installing FreeMoCap in our Installation Guide, but sometimes things don't go as smoothly as planned. This guide will help you work through common problems encountered while installing the software, and hopefully get FreeMoCap running in no time. At the bottom of the page is a list of common error messages you may see during installation, along with common solutions.

If you're still having problems installing FreeMoCap after troubleshooting with the tips below, reach out to us on our Discord to ask for more help.

## Use a New Environment​

Different python projects have different dendencies, and often those dependencies can clash with each other. If you have any installation problem, our first advice is to try installing and running FreeMoCap in a new, dedicated environment. There's many options for creating and managing environments in Python - we recommend Poetry and Conda.

## Check your Python Version​

Currently, FreeMoCap works on Python versions 3.9 through 3.12. We recommend using the most recent compatible version of Python. If installing FreeMoCap in a 3.12 environment doesn't work for you, then try it with a different python version and see if that helps.

## Check your FreeMoCap Version​

FreeMoCap is under active development, and we try to address bugs as quickly as we can. It is always best to install the latest version of the software. If a prior installation isn't working, you can update versions by running pip install freemocap --upgrade.

When pip begins installing the software, it will print which version it is installing. You can compare that to the most recent version listed on PyPi to make sure it is up to date.

## Common Error Messages​

### Command "freemocap" not recognized​

- On some python installations, you may need to type python -m freemocap instead of just freemocap to launch the gui.

### qt.qta.plugin: Could not load the Qt platform plugin "xcb"​

- On linux, some sommon distributions do not come with all of the libraries that are required to run Qt. Most users have been able to fix this by running:

sudo apt-get install '^libxcb.*-dev' libx11-xcb-dev libglu1-mesa-dev libxrender-dev libxi-dev libxkbcommon-dev libxkbcommon-x11-dev

If you use a different package manager, you may need look up equivalent commands for your package manager.

- Use a New Environment

- Check your Python Version

- Check your FreeMoCap Version

- Common Error Messages

- Command "freemocap" not recognized

- qt.qta.plugin: Could not load the Qt platform plugin "xcb"
