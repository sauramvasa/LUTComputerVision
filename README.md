# Lookup-Table Neural Networks for Image Classification

An exploratory research project investigating lookup-table (LUT) layers as alternatives to conventional convolutional neural networks (CNNs).

The project uses fruit-image classification as a test case and compares:

- Standard PyTorch CNNs
- Simplified CNN baselines
- Fully custom NumPy-based lookup-table layers
- LUT convolutional layers
- LUT classifiers
- Hybrid LUT-convolution plus linear-classifier models
- Rewiring strategies for selecting lookup-table comparisons
- Surrogate-gradient and soft-comparison approaches

The repository also includes a synthetic line-pattern dataset for testing whether LUT layers can learn simple visual structures in a controlled environment.

> **Project status:** Exploratory research prototype  
> The notebooks contain multiple experiments, model variants, diagnostic tools, and partially implemented ideas. They are not currently organized as a single reproducible training pipeline.

---

## Motivation

Convolutional neural networks rely on learned matrix multiplications and convolution operations. This project explores whether some of these operations can be replaced by lookup tables based on comparisons between input values.

A lookup-table layer in this project generally:

1. Selects pairs of values from an input vector or image patch.
2. Compares the values in each pair.
3. Converts the comparison results into a binary table index.
4. Uses the index to retrieve a learned value from a lookup table.
5. Combines outputs from multiple tables.

Because the comparison operation is discrete and not directly differentiable, the project experiments with surrogate-gradient methods to train the lookup-table parameters.

---

## Project Goals

The notebooks investigate several questions:

- Can a standard CNN classify fresh and rotten fruits?
- Can a lookup-table classifier use features extracted by a CNN?
- Can lookup-table layers replace conventional convolutional layers?
- How do the number of tables and comparisons affect performance?
- Do lookup-table rows specialize during training?
- Do lookup-table comparisons produce class-separating representations?
- How does gradient information flow through custom LUT layers?
- Can lookup-table anchors be rewired based on data coverage or class separation?
- How do LUT models compare with standard CNN baselines of similar size?

---

## Data

Fruit dataset
The fruit experiments reference the following dataset:

[Fresh and Rotten Fruits Dataset](https://data.mendeley.com/datasets/rg254yr63x/1)

GTS, GTS (2025), “Fruits Dataset for Classification”, Mendeley Data, V1, doi: 10.17632/rg254yr63x.1

---

## Research Notebook Status

The code in this repository was developed as exploratory research in Jupyter notebooks. It contains multiple model variants, diagnostic experiments, parameter sweeps, and partially completed approaches that document the development process.

The notebooks are not currently organized as a production-ready Python package. Some cells depend on previous execution order, and several experiments use different model configurations.

For a concise overview of the project and its results view FinalBIOEREUPoster - Summer '26.pdf

The presentation summarizes the main research question, model architecture, experimental comparisons, and conclusions.