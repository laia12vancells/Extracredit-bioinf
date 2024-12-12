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


# DNA Sequence Generation and Analysis

This project provides a set of functions to generate random DNA sequences, simulate sequencing processes, and analyze the resulting data using De Bruijn graphs. The main functionalities include generating random DNA sequences, adding repeats, simulating sequencing reads, introducing sequencing errors, generating k-mers, constructing De Bruijn graphs, tracing contigs, plotting graphs, and estimating the number of contigs using the Lander-Waterman equation.

## Requirements

- Python 3.x
- `networkx`
- `matplotlib`

You can install the required packages using pip:

```bash
pip install networkx matplotlib
```

## Functions

### 1. `generate_random_dna(length, freq={'A': 0.25, 'C': 0.25, 'G': 0.25, 'T': 0.25})`
Generates a random DNA sequence of a given length and nucleotide frequencies.

### 2. `add_repeats(sequence, repeat_seq, num_repeats)`
Adds repetitive sequences at random positions in the DNA sequence.

### 3. `simulate_sequencing(sequence, read_length, coverage, error_rate)`
Simulates the sequencing process, generating reads from the DNA sequence.

### 4. `introduce_errors(read, error_rate)`
Introduces random sequencing errors into a read.

### 5. `generate_kmers(reads, kmer_length)`
Generates k-mers from a list of sequencing reads.

### 6. `construct_de_bruijn_graph(kmers)`
Constructs a De Bruijn graph from a list of k-mers.

### 7. `trace_contigs(G)`
Traces contigs in the De Bruijn graph by following unambiguous paths.

### 8. `plot_de_bruijn_graph(G)`
Plots the De Bruijn graph.

### 9. `lw_number_of_contigs(genome_length, read_length, coverage)`
Estimates the expected number of contigs based on the Lander-Waterman equation.

## Example Usage

```python
import random
import networkx as nx
import matplotlib.pyplot as plt

# Generate a random DNA sequence
sequence = generate_random_dna(100, {'A': 0.3, 'C': 0.2, 'G': 0.2, 'T': 0.3})

# Add repeats to the sequence
sequence = add_repeats(sequence, 'ATGCGATGCA', 5)

# Simulate sequencing reads
reads = simulate_sequencing(sequence, 100, 30, 0.01)

# Generate k-mers from the reads
kmers = generate_kmers(reads, 21)

# Construct the De Bruijn graph
G = construct_de_bruijn_graph(kmers)

# Trace contigs in the graph
contigs = trace_contigs(G)

# Plot the De Bruijn graph
plot_de_bruijn_graph(G)

print("Number of contigs traced:", len(contigs))
```

## Testing with Lander-Waterman Equation

The script includes a function to test the assembly process using the Lander-Waterman equation:

```python
def test_assembly_with_lander_waterman(sequence_length, read_length, coverage, error_rate, repetitions=5):
    contig_counts = []
    lw_predictions = []
    for _ in range(repetitions):
        sequence = generate_random_dna(sequence_length)
        reads = simulate_sequencing(sequence, read_length, coverage, error_rate)
        kmers = generate_kmers(reads, 21)
        G = construct_de_bruijn_graph(kmers)
        contigs = trace_contigs(G)
        contig_counts.append(len(contigs))
        lw_prediction = lw_number_of_contigs(sequence_length, read_length, coverage)
        lw_predictions.append(lw_prediction)
    avg_contigs = sum(contig_counts) / repetitions
    avg_lw_prediction = sum(lw_predictions) / repetitions
    return avg_contigs, avg_lw_prediction

# Run tests with different parameters
sequence_lengths = [1000, 5000, 10000]
read_length = 100
coverage_levels = [10, 20, 30]
error_rates = [0.0, 0.01, 0.05]

for seq_len in sequence_lengths:
    for cov in coverage_levels:
        for err in error_rates:
            avg_contigs, avg_lw = test_assembly_with_lander_waterman(seq_len, read_length, cov, err)
            print(f"Seq len: {seq_len}, Cov: {cov}, Error rate: {err}")
```





