# Compilation correctness from Promising 1.0 to IMM

## Related papers
<img align="right" width="350" src="https://github.com/anlun/publicFiles/raw/master/pictures/spider.png">

- **[POPL19]** *Bridging the Gap Between Programming Languages and Hardware Weak Memory Models*
  <br />
  [[Paper](https://doi.org/10.1145/3290382) | [arXiv](https://arxiv.org/abs/1807.07892) |
[POPL19 arifact release](https://doi.org/10.5281/zenodo.1484024)]
  <br />
  Anton Podkopaev, Ori Lahav, and Viktor Vafeiadis

## Building the Project

### Requirements
* [Coq 8.9.1](https://coq.inria.fr)
* [Hahn library](https://github.com/vafeiadis/hahn) (`coq-hahn`)
* [The Coq development of IMM](https://github.com/weakmemory/imm) (`coq-imm.1.2`)

### Building Manually

To build the project, one needs to install some libraries (`imm`, `promising-coq`, `hahn`, `coq-imm.1.2`), which the project
depends on. This might be done by running `./configure`.
The command installs `Coq` as well. After that, one needs to run `make` (or `make -j4` for a faster build).

## Description of code and its relation to **Sections 6 and 7** of the **[Podkopaev-al:POPL19]** paper
  - *Promise.v*—a definition of a Promise outcome (**Def. 6.1**).
  - *PromiseFuture.v*— a proof that it is enough to show certification
    only for a restricted set of future memories (**Remark 3**).
  - *SimulationRel.v*—a simulation relation (**Section 7.3**).
  - *SimulationPlainStep.v*— a proof of simulation step (**Prop. 7.8**).
  - *PlainStepBasic.v*,
    *WritePlainStep.v*,
    *FencePlainStep.v*,
    *RMWPlainStep.v*,
    *ReadPlainStep.v*,
    *ReadPlainStepHelper.v*—auxiliary lemmas for the simulation step proof.
  - *SubExecution.v*,
    *CertCOhelper.v*,
    *CertExecution1.v*,
    *CertExecution2.v*,
    *Receptiveness.v*, *CertGraphInit.v*—construction of the certification graph and proofs of its properties (**Section 7.4**).
  - *PromiseToIMMs.v*—a proof of the compilation correctness from Promise to IMMs (**Prop. 6.8 and 6.9, Thm. 7.1**).

Auxiliary files:
*MaxValue.v*,
*Event\_imm\_promise.v*,
*SimStateHelper.v*,
*SimulationPlainStepAux.v*,
*SimulationRelAux.v*,
*ViewRel.v*,
*MemoryAux.v*.
