# PEGylation

[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/polyply/PEGylation/main?labpath=tutorial_data%2FPEGylatedProteins.ipynb)

Tutorial and example data for PEGylating proteins using [polyply](https://github.com/marrink-lab/polyply_1.0) and the Martini 3 coarse-grained force field.

Enhancement of proteins by conjugation with polymers (PEGylation) is an active area of research, but the interactions between polymers and proteins are far from fully understood. This tutorial demonstrates how to set up molecular dynamics (MD) simulations of protein-polymer conjugates using the latest iteration of the Martini coarse-grained (CG) force field.

## Quick start

Click the **launch binder** badge above to run the tutorial notebook (`tutorial_data/PEGylatedProteins.ipynb`) directly in your browser — no local installation required.

> **Note:** the first Binder build can take 10–20 minutes since GROMACS and its dependencies need to be compiled/fetched from conda. Subsequent launches are much faster thanks to Binder's build cache.
>
> Binder sessions are ephemeral and memory-limited (~2GB RAM), so they're suited for working through the tutorial and generating starting structures/topologies, not for production MD runs.

## Repository contents

```
tutorial_data/
├── PEGylatedProteins.ipynb   # main tutorial notebook
├── 3LZT.cif, 3lzt.pdb, ...   # example protein structure (lysozyme) and intermediates
├── martini_v3.0.0*.itp       # Martini 3 force field files
├── go_atomtypes.itp, go_nbparams.itp   # Go-model parameters
└── cg_mdps/                  # GROMACS .mdp files for CG simulations
```

## Prerequisites

If you'd rather run the notebook locally instead of on Binder, you'll need:

- [polyply](https://github.com/marrink-lab/polyply_1.0) (GitHub version):
  ```bash
  pip install git+https://github.com/fgrunewald/polyply_1.0.git#polyply_1.0
  ```
- [Protein Repair and Analysis Server (PRAS)](https://pypi.org/project/Pras-Server/):
  ```bash
  pip install Pras-Server==1.2.1
  ```
- [vermouth-martinize](https://github.com/marrink-lab/vermouth-martinize) — installed automatically alongside polyply
- [cgsmiles](https://pypi.org/project/cgsmiles/):
  ```bash
  pip install cgsmiles
  ```
- [GROMACS](https://www.gromacs.org/):
  ```bash
  conda install -c bioconda -c conda-forge gromacs
  ```
- [GromacsWrapper](https://gromacswrapper.readthedocs.io/):
  ```bash
  pip install GromacsWrapper
  # or: conda install -c conda-forge gromacswrapper
  ```
- [DSSP](https://github.com/PDB-REDO/dssp) (`mkdssp`, required by `martinize2 -dssp`):
  ```bash
  conda install -c conda-forge dssp
  ```
- The Martini 3 [force field files](https://github.com/marrink-lab/martini-forcefields/tree/main/martini_forcefields/regular/v3.0.0/gmx_files) — already bundled in `tutorial_data/` for this tutorial.

An `environment.yml` is provided in this repository root and covers all of the above (used automatically by Binder). To build the same environment locally with conda/mamba:

```bash
git clone https://github.com/polyply/PEGylation.git
cd PEGylation
conda env create -f environment.yml
conda activate pegylation
jupyter lab tutorial_data/PEGylatedProteins.ipynb
```

## Citation

If you use polyply or this tutorial in your research, please cite the [polyply publication](https://www.nature.com/articles/s41467-021-25874-z) and the [Martini 3 force field](https://www.nature.com/articles/s41592-021-01098-3).

## License

See [LICENSE](LICENSE) for details.
