# EquiChain: A Machine-Learning-Based Sharded PBFT Blockchain

## Overview

EquiChain is a permissioned blockchain framework that combines:

* Multi-Task Learning (MTL) for node behavior classification,
* Credit-based Round Robin shard formation,
* PBFT consensus within shards,
* Dynamic committee reconfiguration,
* Leader replacement through view-change mechanisms,
* Performance evaluation under different node behaviors.

The objective of EquiChain is to improve the scalability and reliability of PBFT-based blockchains by identifying reliable participants and distributing them across committees using a score-driven sharding strategy.

This repository contains the prototype implementation used for the experimental evaluation presented in the associated publication.

---

## Implemented Components

### Consensus Layer

* PBFT consensus protocol
* Pre-prepare, prepare, commit, and reply phases
* Checkpoint generation
* View-change and leader replacement mechanisms

### Sharding Layer

* Dynamic shard formation
* Primary node selection
* Credit-based Round Robin shard assignment
* Periodic shard reconfiguration

### Node Classification Layer

* Multi-Task Learning (MTL) classifier
* Behavioral prediction of:

  * Rapidity
  * Availability
  * Honesty
  * Fault type

### Fault Injection

The framework supports multiple node behaviors:

* Honest nodes
* Slow nodes
* Byzantine nodes
* Non-responding nodes
* Faulty primary nodes
* Faulty reply nodes
* DoS attackers
* Digest-modification attackers

### Evaluation Metrics

The prototype collects:

* Transaction latency
* Block confirmation delay
* Communication overhead
* Classification accuracy
* Number of exchanged messages
* Leader changes
* Node participation statistics

---

## Repository Structure

```text
.
├── main.py                  # Experiment launcher
├── PBFT.py                  # Consensus and sharding mechanisms
├── client.py                # Client requests and validation
├── settings.py              # Classification and evaluation
├── mtl-models/              # Trained MTL models
├── messages_formats/        # Message templates
├── ports.json               # Communication configuration
└── nodes_data.csv           # Generated node statistics
```

---

## Requirements

Python 3.10+

Required packages:

```bash
pip install pynacl numpy pandas scikit-learn
```

---

## Running EquiChain

Launch the system:

```bash
python main.py
```

The framework will:

1. Start blockchain nodes.
2. Create clients.
3. Execute PBFT consensus.
4. Generate transactions.
5. Create blocks.
6. Classify nodes using the trained MTL model.
7. Reconfigure committees and shards.
8. Collect performance metrics.

---

## Experimental Scenarios

The numbers of Byzantine, slow, unavailable, and faulty nodes can be configured in:

```python
main.py
```

Example:

```python
nbn = 4      # Byzantine nodes
nsn = 2      # Slow nodes
nnrn = 1     # Non-responding nodes
```

This allows reproducing different fault scenarios.

---

## Reproducibility

The experiments reported in the paper were conducted using this implementation.

To reproduce the results:

1. Configure the desired network size in `settings.py`.
2. Configure node behaviors in `main.py`.
3. Execute `python main.py`.
4. Collect generated metrics and logs.

---

## Limitations

This prototype is intended for research and experimentation.

Current limitations include:

* Single-machine deployment
* Limited-scale evaluation
* No WAN deployment
* No smart-contract layer
* No production-grade networking stack

These limitations do not affect the evaluation of the proposed classification, sharding, and consensus mechanisms but leave room for future extensions.
