# Extracredit-bioinf

# Sequence Evolution Simulation

## Overview

This project simulates the evolution of amino acid sequences using the BLOSUM62 substitution matrix. It generates phylogenetic trees, calculates sequence distances, and evaluates tree rearrangements. The simulation considers mutation, extinction, and speciation probabilities to model natural evolutionary processes.

## Requirements

- Python 3.x
- Libraries:
  - `random`
  - `numpy`
  - `Bio.Phylo`
  - `Bio.Phylo.Newick`
  - `io.StringIO`
  - `collections.defaultdict`
  - `Bio.pairwise2`
  - `Bio.Align.substitution_matrices`
  - `matplotlib.pyplot`

## Installation

To install the required libraries, you can use `pip`:

```bash
pip install numpy biopython matplotlib
```

## Usage

1. **Loading BLOSUM62 Matrix**: The BLOSUM62 substitution matrix is loaded to facilitate sequence comparisons.
2. **Sequence Mutation**: A function mutates amino acid sequences based on a specified mutation rate, introducing random changes.
3. **Simulating Evolution**: This function simulates the evolution of sequences over time, generating multiple descendant sequences and tracking their evolutionary history. It considers hyperparameters such as:
   - Number of leaf sequences to generate
   - Mutation rate
   - Extinction probability (set to 0.1)
   - Speciation probability (set to 0.2)
4. **Generating Newick Tree**: A phylogenetic tree is generated from the evolutionary history and exported in Newick format.
5. **Calculating BLOSUM62 Distance**: The BLOSUM62 distance between sequences is calculated using global alignment.
6. **Drawing Phylogenetic Tree**: The phylogenetic tree is visualized using Matplotlib.
7. **Plotting Distance Comparisons**: Histograms are plotted to compare original and rearranged distances.
8. **Evaluating Tree Rearrangement**: The effectiveness of tree rearrangement is evaluated by comparing the sum of pairwise distances before and after rearrangement.

```





