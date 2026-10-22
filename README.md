# Joint ML-KEM Key Generation against Algorithm Substitution Attacks

This repository contains the companion proof document for **Joint ML-KEM Key Generation against Algorithm Substitution Attacks**. It provides the protocol specification, security experiments, simulators, and reductions for a two-party ML-KEM service designed to resist ASA-induced private-key recovery.

**[Read the full proof](proof.pdf)** | **[BibTeX citation](citation.bib)**

## Overview

An algorithm substitution attack on local key generation can encode private-key information in public outputs. The framework combines independent random contributions from a receiver Alice and a protected online helper Bob, and retains private state as shares. It releases the public matrix seed before expansion and authenticates the private state consumed across computation stages.

The document studies private-key recovery in two separate experiments.

1. **Substituted Alice with protected Bob.** An external decoder receives Alice's complete execution view.
2. **Honest Alice with passive Bob.** Bob retains his complete execution view, including setup and component randomness, messages, intermediate configurations, outputs, and his own encapsulation keys.

Both experiments test recovery against a fresh independent encapsulation after the candidate private key has been fixed. The analysis accounts for selection among generation attempts and information retained from interrupted executions, including anchors that have not yet been delivered.

## Reading guide

The current companion document is **version 43, 70 pages**. The page numbers below refer to the PDF.

| Topic | Pages |
| --- | --- |
| Scope, assumptions, and security experiments | 1, 5 |
| Forward call-local composition | 8 |
| Recovery from substituted Alice's view | 19-20 |
| Recovery from passive Bob's complete view | 22-27 |
| Interrupted execution with an undelivered anchor | 28 |
| Application interface and public-trace closure | 40-42 |
| Placement-specific recovery and circuit cost | 48-50 |

Start with the scope and experiments, then follow the two recovery arguments. Later sections include circuit inventories, experimental discussion, and historical cost appendices with their own stated scope.

## Security and evidence scope

The proofs consider classical, static, sequential executions under the channel, protected-owner, commitment, component-simulation, and application-interface assumptions specified in the document.

The model keeps result joining and private AEAD/command processing inside the protected application. Public responses and subsequent controller requests follow the declared public-history interface.

Corrected Lindell-Pinkas two-party computation provides the theoretical realization under its stated assumptions. Native EMP results provide separate functional and resource evidence for the same stage functions. Finite diagnostic checks support the stated accounting and interface policies; the mathematical arguments are given in the document.

## Repository contents

| File | Description |
| --- | --- |
| [`proof.pdf`](proof.pdf) | Full specification, simulators, and security reductions |
| [`citation.bib`](citation.bib) | BibTeX entry for the companion proof |
| [`README.md`](README.md) | Overview and reading guide |

## Citation

Please cite the companion proof using the entry in [`citation.bib`](citation.bib).

```bibtex
@unpublished{shaov43proof,
  author = {Yan Shao and Yuejun Liu and Yongbin Zhou and Wei Cheng and Jingdian Ming and Liehuang Zhu},
  title = {Joint {ML-KEM} Key Generation against Algorithm Substitution Attacks: Full Specification, Simulator and Reductions},
  note = {Companion proof document, version 43},
  year = {2026},
  month = oct
}
```
