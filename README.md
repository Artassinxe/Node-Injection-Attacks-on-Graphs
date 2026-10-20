# Node Injection Attacks on Graphs

Group project for the **Graph Mining and Social Networks** course. The project studies adversarial node injection attacks and the robustness of text-attributed graphs (TAGs), where node features are derived from text such as user profiles, comments, or paper abstracts.

The project brief is available in [`doc/main.pdf`](doc/main.pdf), with its LaTeX source in [`doc/main.tex`](doc/main.tex). The repository currently contains the project brief; the practical demonstration is part of the planned work.

## Project Overview

In a graph injection attack (GIA), an attacker adds malicious nodes and their incident edges to an existing graph. Unlike edge-modification attacks, this threat model does not require changing relationships between existing users. A graph neural network (GNN) can propagate the injected nodes' influence to legitimate neighbors through message passing, potentially changing their predictions.

The project focuses on realistic attacks against text-attributed graphs. An attacker cannot directly submit an arbitrary dense feature vector when node attributes come from natural language: the injected profile must be expressed as text and then represented by the model. The brief covers the transition from continuous-feature attacks such as TDGIA to text-level approaches such as WTGIA / ITGIA and GraphTextack.

## Objectives

- Formalize the node-injection threat model and its constraints, including an injection budget and a limit on each injected node's degree.
- Explain how injected nodes can increase the GNN's misclassification rate on legitimate target nodes.
- Study text-level injection attacks on TAGs, including sparse embedding generation and the conversion of embeddings into natural-language text.
- Explore a defensive approach combining random-walk path masking with a differentially private mixture of experts (DMGAN + DPMoE).
- Prepare a demonstration that compares a standard GCN with structural filtering or denoising under progressively larger injection attacks.

## Planned Demonstration

The project brief proposes the following experiment:

1. Train or evaluate a standard GCN on a clean citation graph.
2. Progressively inject malicious nodes, from 10 up to 300, with strategically selected connections.
3. Track the model's accuracy on the target neighborhood as the attack grows.
4. Apply a structural defense, such as pruning or denoising, and compare the results.

Candidate datasets are **Cora**, **CiteSeer**, and **ogbn-arxiv**. The brief suggests starting with Cora. Candidate tools include **PyTorch Geometric**, **DeepRobust**, and the **Graph Robustness Benchmark (GRB)**. Dataset choice, attack configuration, and the final defense implementation remain to be established as the demonstration is developed.

## Team

- Anthony Chaigneau
- Mathias Tortoza
- Ahmad CHOUMAN
- Thibault COLIN
- Hugo GARCIA

## Presentation and Deliverables

The assessment format in the project brief is a 15-minute oral presentation, a 5-minute practical demonstration, and 5 minutes for questions. The expected deliverables are presentation slides, reference papers, and the demonstration's source code.

## References

- Sun, Y., et al. (2023). “Let Graph be the Go Board: Gradient-free Node Injection Attack for Graph Neural Networks via Reinforcement Learning.” AAAI 2023.
- Lukas, J., et al. (2023). “Adversarial Training for Graph Neural Networks: Pitfalls, Solutions, and New Directions.” NeurIPS 2023.
- Lei, R., et al. (2024). “Text-Level Graph Injection Attacks on Text-Attributed Graphs (WTGIA / ITGIA).” NeurIPS 2024.
- Zhang, H., et al. (2025). “Robustness Inspired Graph Backdoor Defense.” ICLR 2025.

## Building the Project Brief

With `latexmk` installed, build the PDF from the `doc/` directory:

```sh
cd doc
latexmk -pdf main.tex
```

LaTeX auxiliary build files are excluded from Git tracking.
