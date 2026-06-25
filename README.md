
# DNA Sequence Analyzer
# written by Sayan Mahajan

# Count A, T, G, and C nucleotides
def count_nucleotides(dna):

    counts = {
        "A": dna.count("A"),
        "T": dna.count("T"),
        "G": dna.count("G"),
        "C": dna.count("C")
    }
    return counts

# Calculate GC content percentage
def calculate_gc_content(dna):
    
    gc_count = dna.count("G") + dna.count("C")
    return (gc_count / len(dna)) * 100 if len(dna) > 0 else 0


# Generate reverse complement of DNA sequence
def reverse_complement(dna):
  
    complement = {
        "A": "T",
        "T": "A",
        "G": "C",
        "C": "G"
    }

    rev_comp = "".join(complement[base] for base in reversed(dna))
    return rev_comp

# Convert DNA sequence to RNA sequence
def transcribe_dna_to_rna(dna):
   
    return dna.replace("T", "U")

# main function
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