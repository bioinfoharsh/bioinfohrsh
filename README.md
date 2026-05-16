# bioinfohrsh
DNA sequence analysis project using python for basic bioinformatics operations

# DNA Sequence Analysis Project

# Input DNA sequence
dna = input("Enter DNA Sequence: ").upper()

# Function to validate DNA
def validate_dna(seq):
    valid_nucleotides = ['A', 'T', 'G', 'C']
    for nucleotide in seq:
        if nucleotide not in valid_nucleotides:
            return False
    return True

# Validate sequence
if validate_dna(dna):

    print("\nValid DNA Sequence\n")

    # Sequence Length
    print("Sequence Length:", len(dna))

    # Nucleotide Count
    print("\nNucleotide Count:")
    print("A:", dna.count('A'))
    print("T:", dna.count('T'))
    print("G:", dna.count('G'))
    print("C:", dna.count('C'))

    # GC Content
    gc_content = ((dna.count('G') + dna.count('C')) / len(dna)) * 100
    print("\nGC Content: {:.2f}%".format(gc_content))

    # Complementary Sequence
    complement = dna.replace('A', 't') \
                    .replace('T', 'a') \
                    .replace('G', 'c') \
                    .replace('C', 'g').upper()

    print("\nComplementary Sequence:")
    print(complement)

    # Reverse Complement
    reverse_complement = complement[::-1]

    print("\nReverse Complement:")
    print(reverse_complement)

    # DNA to RNA Transcription
    rna = dna.replace('T', 'U')

    print("\nRNA Sequence:")
    print(rna)

    # Simple Protein Translation
    codon_table = {
        'ATA':'I', 'ATC':'I', 'ATT':'I', 'ATG':'M',
        'ACA':'T', 'ACC':'T', 'ACG':'T', 'ACT':'T',
        'AAC':'N', 'AAT':'N', 'AAA':'K', 'AAG':'K',
        'AGC':'S', 'AGT':'S', 'AGA':'R', 'AGG':'R',
        'CTA':'L', 'CTC':'L', 'CTG':'L', 'CTT':'L',
        'CCA':'P', 'CCC':'P', 'CCG':'P', 'CCT':'P',
        'CAC':'H', 'CAT':'H', 'CAA':'Q', 'CAG':'Q',
        'CGA':'R', 'CGC':'R', 'CGG':'R', 'CGT':'R',
        'GTA':'V', 'GTC':'V', 'GTG':'V', 'GTT':'V',
        'GCA':'A', 'GCC':'A', 'GCG':'A', 'GCT':'A',
        'GAC':'D', 'GAT':'D', 'GAA':'E', 'GAG':'E',
        'GGA':'G', 'GGC':'G', 'GGG':'G', 'GGT':'G',
        'TCA':'S', 'TCC':'S', 'TCG':'S', 'TCT':'S',
        'TTC':'F', 'TTT':'F', 'TTA':'L', 'TTG':'L',
        'TAC':'Y', 'TAT':'Y', 'TAA':'_', 'TAG':'_',
        'TGC':'C', 'TGT':'C', 'TGA':'_', 'TGG':'W',
    }

    protein = ""

    for i in range(0, len(dna)-2, 3):
        codon = dna[i:i+3]
        protein += codon_table.get(codon, '?')

    print("\nProtein Sequence:")
    print(protein)

else:
    print("\nInvalid DNA Sequence!")