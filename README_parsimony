# Overview
This Python script simulates the evolution of sequences, constructs phylogenetic trees, and evaluates tree-reconstruction methods based on evolutionary distance metrics. The program uses the Biopython library for handling phylogenetic trees, NumPy for matrix operations, and Matplotlib for visualization.

## Features

### Simulate Evolution:
- Mutates a sequence over time with a specified mutation rate.
- Incorporates speciation and extinction probabilities.
- Tracks the evolution of sequences across generations.

### Phylogenetic Tree Generation:
- Constructs a phylogenetic tree in Newick format based on simulated evolutionary history.
- Visualizes the tree structure using Matplotlib.

### Distance Calculation:
- Calculates pairwise distances between sequences using the BLOSUM62 substitution matrix.
- Evaluates the similarity of reconstructed trees to true evolutionary distances.

### Tree Reconstruction and Evaluation:
- Implements the UPGMA method for clustering.
- Evaluates tree-reconstruction accuracy using root mean square (RMS) differences.

### Graphical Output:
- Generates histograms to compare pairwise distances before and after tree rearrangement.

## Requirements

### Python Libraries
- Biopython (`pip install biopython`)
- NumPy (`pip install numpy`)
- Matplotlib (`pip install matplotlib`)

## Key Functions

### 1. Simulating Evolution
- `mutate_sequence(sequence, mutation_rate)`: Introduces mutations into a sequence based on the mutation rate.
- `simulate_evolution(sequence, num_leaf_sequences, mutation_rate, extinction_prob, speciation_prob)`: Simulates the evolutionary process, including mutation, speciation, and extinction.

### 2. Phylogenetic Tree Operations
- `generate_newick(tree_history)`: Constructs a Newick-formatted tree from evolutionary history.
- `draw_tree(tree)`: Visualizes the phylogenetic tree using Matplotlib.

### 3. Distance Calculations
- `blosum62_distance(seq1, seq2)`: Computes the BLOSUM62 score between two sequences.
- `calculate_rms(true_distances, estimated_distances)`: Calculates the RMS difference between true and estimated distances.

### 4. Tree Reconstruction
- `upgma(distance_matrix)`: Constructs a tree using the UPGMA method.
- `evaluate_tree_rearrangement(tree, distance_matrix)`: Evaluates the effectiveness of tree rearrangement.

## How to Use

### Run the Script:
Execute the script directly with `python <script_name>.py`.

### Main Workflow:
1. A starting sequence is generated.
2. Simulated evolution produces descendant sequences.
3. A phylogenetic tree is constructed and visualized.
4. Pairwise distances are calculated for evaluation.
5. Tree-reconstruction methods (e.g., UPGMA) are tested and compared.

### Customization:
- Adjust evolutionary parameters (`mutation_rate`, `extinction_prob`, `speciation_prob`) for different simulations.
- Change the number of leaf sequences (`num_leaf_sequences`) or trees (`num_trees`).

## Output
- **Tree Visualization**: Displays the tree structure using Matplotlib.
- **Distance Metrics**: Prints RMS differences for each evolutionary distance tested.
- **Histograms**: Compares pairwise distances before and after tree rearrangement.

## Example Usage

```python
start_sequence = "ACDEFGHIKLMNPQRSTVWY" * 10
num_leaf_sequences = 20
mutation_rate = 0.05

# Simulate evolution
sequences, tree_history, mutation_counts = simulate_evolution(
    start_sequence, num_leaf_sequences, mutation_rate
)

# Generate and visualize tree
phylo_tree = generate_newick(tree_history)
draw_tree(phylo_tree)

# Evaluate reconstruction
evaluate_upgma_fitch_margoliash(sequences, mutation_counts, [50, 100, 200])
