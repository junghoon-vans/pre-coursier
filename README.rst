============
pre-coursier
============

The ``pre-coursier`` make it easy to run JVM tools on pre-commit.

Requirements
============

The following tools must be installed:

- pre-commit_ >= 2.8.0
- coursier_

Getting started
===============

Setup pre-commit hooks
----------------------

Add the following to your ``.pre-commit-config.yaml``:

.. parsed-literal::

  repos:
  - repo: https://github.com/junghoon-vans/pre-coursier
    rev: |release|
    hooks:
    - id: scalafmt
      args: ["--config-str", "version = 3.7.14, runner.dialect = scala3"]

Install pre-commit
------------------

.. code:: bash

  pre-commit install

Run pre-commit
--------------

.. code:: bash

  git add . # Add changes
  git commit -m "Run pre-commit"

This will run ``scalafmt`` on all ``*.scala|*.sc|*.sbt`` files.

  By default, the version of the hook is set to the ``latest`` version.

How to downgrade the version of the hook
========================================

  This feature is available with pre-commit 3.0.0+.

If you want to override the version of the hook, you can set the version of the hook to run with the ``additional_dependencies`` option.

.. parsed-literal::

  repos:
  - repo: https://github.com/junghoon-vans/pre-coursier
    rev: |release|
    hooks:
    - id: scalafmt
      args: ["--config-str", "version = 3.7.14, runner.dialect = scala3"]
      additional_dependencies: ["scalafmt:2.4.2"]

.. _pre-commit: https://pre-commit.com/#install
.. _coursier: https://get-coursier.io/docs/cli-installation

.. |release| replace:: v0.1.0
