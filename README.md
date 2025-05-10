# CyclicSpectrumGenerator

# Description
CyclicSpectrumGenerator is a Python script that computes the theoretical cyclic spectrum of a peptide based on the integer mass of its constituent amino acids. This is a fundamental tool in peptide sequencing by mass spectrometry, especially in algorithms such as Cyclopeptide Sequencing.

Given a linear peptide sequence, the script returns a sorted list of all possible subpeptide masses, including the complete peptide and the empty peptide (mass 0), considering the peptide in cyclic form.

# Functionality
cyclic_spectrum(peptide)
* Purpose: Calculates the cyclic spectrum of a peptide by generating the mass of every possible subpeptide in its circular form.

# Approach:

* Uses a predefined mass table mapping each amino acid to its integer mass.
* Concatenates the peptide to itself to simulate circular subpeptides.
* Computes the total peptide mass and adds mass 0 for the empty subpeptide.
* Generates and sums all cyclic subpeptides of length 1 to n-1.
* Returns a sorted list of masses.

# Parameters
* peptide (str): A string representing a peptide sequence using single-letter amino acid codes (e.g., "PAMHQDLEAVSHY").

# Returns
*List[int]: A sorted list of integers representing the mass spectrum of the cyclic peptide.

# Example Usage
```
def cyclic_spectrum(peptide):
    # Dictionary to store the mass of each amino acid
    mass_table = {
        'G': 57, 'A': 71, 'S': 87, 'P': 97,
        'V': 99, 'T': 101, 'C': 103, 'I': 113,
        'L': 113, 'N': 114, 'D': 115, 'K': 128,
        'Q': 128, 'E': 129, 'M': 131, 'H': 137,
        'F': 147, 'R': 156, 'Y': 163, 'W': 186
    }

    total_mass = sum(mass_table[aa] for aa in peptide)
    spectrum = [0, total_mass]

    n = len(peptide)
    for length in range(1, n):
        for i in range(n):
            subpeptide = (peptide * 2)[i:i + length]
            spectrum.append(sum(mass_table[aa] for aa in subpeptide))

    spectrum.sort()
    return spectrum

# Sample Input
peptide = "PAMHQDLEAVSHY"
result = cyclic_spectrum(peptide)
print(" ".join(map(str, result)))

```

# Output Example:
0 57 71 87 97 101 114 128 129 137 147 163 186 ... <total_mass>

# Applications

* This script is widely applicable in:
* Peptide Sequencing by Mass Spectrometry: Simulating theoretical spectra for matching experimental spectra.
* Bioinformatics Education: Demonstrating circular subpeptide fragmentation.
* Algorithm Development: Used in algorithms like Cyclopeptide Sequencing, Leaderboard Cyclopeptide Sequencing, and Spectral Convolution.
* Proteomics Pipelines: Useful in preprocessing or testing stages of peptide identification workflows.

# Requirements
* Python 3.x
* No external dependencies

# License
This project is licensed under the MIT License – see the LICENSE file for details.








