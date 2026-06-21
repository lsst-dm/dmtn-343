.. image:: https://img.shields.io/badge/dmtn--343-lsst.io-brightgreen.svg
   :target: https://dmtn-343.lsst.io
.. image:: https://github.com/lsst-dm/dmtn-343/workflows/CI/badge.svg
   :target: https://github.com/lsst-dm/dmtn-343/actions/

#####################################################################################
Observing the Observatory. The Observability Journey of the Vera C. Rubin Observatory
#####################################################################################

DMTN-343
========

The Vera C. Rubin Observatory is not only an observatory, it is also a distributed production engine for science. During operations, it will move thousands of images, metadata, and alerts through the telescope, camera, network, storage, and processing services every night. Rubin will produce up to 20 TB of raw data per night (10TB on the wire with compression), with an alert stream that reaches millions of events and a target latency of nearly 1 minute [1-3].

In this environment, simple monitoring is not enough. We need to ask why something changed, where latency started, which component is under pressure, and whether the behavior is connected with the observing conditions or the state of the facility. This paper describes the observability journey of the Vera C. Rubin Observatory DevOps team, a multi-year effort to build, refine, and scale a modern observability stack for one of the most ambitious astronomical facilities ever constructed.

The platform is based on open-source components, and the result is, not only a software stack, it is an operations model. Dashboards and alerts are treated as code; labels are part of the interface between teams; and the observability system is continuously improved as commissioning and operations reveal new questions. The paper highlights dashboard creation strategies, discusses the hard parts: configuration complexity, label discipline, storage and retention trade-offs, human adoption, and the need to keep improving the system rather than calling it finished [4].

Links
=====

- Live drafts: https://dmtn-343.lsst.io
- GitHub: https://github.com/lsst-dm/dmtn-343

Build
=====

This repository includes lsst-texmf_ as a Git submodule.
Clone this repository::

    git clone --recurse-submodules https://github.com/lsst-dm/dmtn-343

Compile the PDF::

    make

Clean built files::

    make clean

Updating acronyms
-----------------

A table of the technote's acronyms and their definitions are maintained in the `acronyms.tex` file, which is committed as part of this repository.
To update the acronyms table in ``acronyms.tex``::

    make acronyms.tex

*Note: this command requires that this repository was cloned as a submodule.*

The acronyms discovery code scans the LaTeX source for probable acronyms.
You can ensure that certain strings aren't treated as acronyms by adding them to the `skipacronyms.txt <./skipacronyms.txt>`_ file.

The lsst-texmf_ repository centrally maintains definitions for LSST acronyms.
You can also add new acronym definitions, or override the definitions of acronyms, by editing the `myacronyms.txt <./myacronyms.txt>`_ file.

Updating lsst-texmf
-------------------

`lsst-texmf`_ includes BibTeX files, the ``lsstdoc`` class file, and acronym definitions, among other essential tooling for LSST's LaTeX documentation projects.
To update to a newer version of `lsst-texmf`_, you can update the submodule in this repository::

   git submodule update --init --recursive

Commit, then push, the updated submodule.

.. _lsst-texmf: https://github.com/lsst/lsst-texmf
