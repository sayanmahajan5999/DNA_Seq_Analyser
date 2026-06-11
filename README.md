
# DNA Sequence Analyzer
# Author: Sayan Mahajan

def count_nucleotides(dna):
    """Count A, T, G, and C nucleotides."""
    counts = {
        "A": dna.count("A"),
        "T": dna.count("T"),
        "G": dna.count("G"),
        "C": dna.count("C")
    }
    return counts


def calculate_gc_content(dna):
    """Calculate GC content percentage."""
    gc_count = dna.count("G") + dna.count("C")
    return (gc_count / len(dna)) * 100 if len(dna) > 0 else 0


def reverse_complement(dna):
    """Generate reverse complement of DNA sequence."""
    complement = {
        "A": "T",
        "T": "A",
        "G": "C",
        "C": "G"
    }

    rev_comp = "".join(complement[base] for base in reversed(dna))
    return rev_comp


def transcribe_dna_to_rna(dna):
    """Convert DNA sequence to RNA sequence."""
    return dna.replace("T", "U")


def main():
    print("-" * 40)
    print("      DNA SEQUENCE ANALYZER")
    print("-" * 40)

    dna = input("Enter a DNA sequence: ").upper()

    # Validate sequence
    valid_bases = {"A", "T", "G", "C"}

    if not all(base in valid_bases for base in dna):
        print("Error: DNA sequence contains invalid characters!")
        return

    # Nucleotide counts
    counts = count_nucleotides(dna)

    # GC content
    gc_content = calculate_gc_content(dna)

    # Reverse complement
    rev_comp = reverse_complement(dna)

    # RNA transcription
    rna = transcribe_dna_to_rna(dna)

    # Results
    print("\n--- Analysis Results ---")
    print(f"Sequence Length : {len(dna)}")
    print(f"A Count         : {counts['A']}")
    print(f"T Count         : {counts['T']}")
    print(f"G Count         : {counts['G']}")
    print(f"C Count         : {counts['C']}")
    print(f"GC Content      : {gc_content:.2f}%")
    print(f"Reverse Complement : {rev_comp}")
    print(f"RNA Transcript     : {rna}")


if __name__ == "__main__":
    main()