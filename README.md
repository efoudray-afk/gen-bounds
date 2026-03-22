# gen-bounds

**Why do neural networks work so well when math says they shouldn't?**

Classical learning theory tells us that a model with millions of parameters should memorize its training data and fail on anything new. But deep neural networks generalize surprisingly well — and nobody fully understands why.

This project tries to make that gap concrete. It computes various theoretical generalization bounds for trained neural networks and compares them to what actually happens in practice. Spoiler: most bounds are hilariously loose. But some (especially PAC-Bayes) are starting to get interesting.

## What this project does

- Trains small neural networks on standard datasets (MNIST, CIFAR-10 subsets)
- Computes generalization bounds from different theoretical frameworks
- Visualizes how tight or loose each bound is compared to real test performance
- Tracks how bounds evolve during training, not just at the end

## Bounds implemented

- **VC-dimension** — the classic baseline (expect this one to be absurdly loose)
- **Rademacher complexity** — data-dependent, slightly more realistic
- **PAC-Bayes** — currently the most promising family of bounds for deep nets
- **Compression-based** — how much can you prune before things break?
- **Norm-based** — spectral norm, Frobenius norm, path-norm variants

## Project structure

```
gen-bounds/
├── bounds/          # one module per bound family
├── models/          # training loops and architectures
├── experiments/     # scripts for running comparisons
├── dashboard/       # interactive visualizations
└── paper/           # writeup in LaTeX
```

## Running experiments

More details coming as the project develops. The rough workflow is:

1. Train a model with full logging (weights, losses, metrics per epoch)
2. Compute all bounds at each checkpoint
3. Plot everything and see which bounds actually track generalization

## Background reading

If you're curious about this stuff, here's where I started:

- Shalev-Shwartz & Ben-David, *Understanding Machine Learning: From Theory to Algorithms* (Ch. 2–4 for the basics)
- Dziugaite & Roy, "Computing Nonvacuous Generalization Bounds for Deep (Stochastic) Neural Networks" (2017) — the paper that showed PAC-Bayes bounds can actually be non-trivial
- Neyshabur et al., "Exploring Generalization in Deep Learning" (2017) — good overview of norm-based approaches

## Status

Early stage — building out the core library and running initial experiments. This is a learning-by-building project, not a polished product (yet).

## License

MIT
