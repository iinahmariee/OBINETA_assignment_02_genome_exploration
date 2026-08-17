# OBIÑETA_assignment_02_genome_exploration
# Name: Obiñeta, Inah Marie A.

# Activity Title: Basic Genome Structure and Sequence Exploration Using Galaxy
BIO 300 –B Cell and Molecular Biology Laboratory

# Species: *Cynopterus brachyotis* (lesser short-nosed fruit bat) genome assembly (GCA_009793145.1)

# Objectives
To describe the structure of a genome assembly using basic statistics, sequence-length filtering, and a small-scale open reading frame (ORF) exploration and learning to inspect and interpret an assembled genome.

# Tools used in Galaxy
# Part 1 — Genome Download
- Source: NCBI FTP
- File: GCA_009793145.1_ASM979314v1_genomic.fna.gz
- Renamed in Galaxy to: **Cynopterus_brachyotis_genome_original.fna.gz**
  
# Part 2 — Assembly Statistics
- Tool: *gfastats*
- Tool mode: Summary statistics generation
- Report mode: Genome assembly statistics (--nstar-report)
- Input file: **1: Cynopterus_brachyotis_genome_original.fna.gz**
- Output renamed to: **Cynopterus_brachyotis_Assembly_Statistics_gfastats**

# Part 3 — Sequence-Length Structure
- Tool: *Compute sequence length*
- Input file: **1: Cynopterus_brachyotis_genome_original.fna.gz**
- Setting: "Strip fasta description from header?" = Yes
- Output: **Compute sequence length on dataset 1**
- Sorted using Galaxy's *Sort* tool (column 2, descending) to identify the top 5 longest sequences

# Part 4 — Length-Filtering Experiment
- Step 1: Tool: *Filter sequences by length*
  - Input file: **1: Cynopterus_brachyotis_genome_original.fna.gz**
  - Parameter: minimum length = 10,000 bp (10 kb)
  - Output renamed to: **Cynopterus_brachyotis_filtered_10kb**
- Step 2
  - Re-ran *gfastats* (same settings as Part 2) using input file: **5: Cynopterus_brachyotis_filtered_10kb**
  - Output renamed to: **Cynopterus_brachyotis_Filtered_10kb_Assembly_Statistics_gfastats**

# Part 5 — Small ORF Exploration
- Step 1: Tool: *Filter sequences by ID from a tabular file*
  - Input file: **1: Cynopterus_brachyotis_genome_original.fna.gz**
  - Filter using ID list from: "provided list"
  - My ID: SSHV01000001.1 (112,931 bp)
  - Output: "Positive matches only"
  - Output renamed to: **7: Cynopterus_brachyotis_genome_original.fna uncompressed with matched ID**
- Step 2: Tool: getorf
  - Input file: **7: Cynopterus_brachyotis_genome_original.fna uncompressed with matched ID**
  - Minimum nucleotide size of ORF to report: 300
  - What to output: Translation of regions between STOP codons
  - All START codons to code for Methionine: Yes
  - Circular sequence: No
  - Output: **Cynopterus_brachyotis_getorf.fasta**

 # Short Interpretation
The *Cynopterus brachyotis* assembly is highly fragmented — spread across 48,006 scaffolds with a maximum length of only 4.5 Mb, far short           of a full chromosome. Short sequences dominate by count of about 74% but contribute little to total genome size (4.6%), showing that           most real genetic content sits in a smaller set of longer scaffolds. GC content (39%) falls within the normal mammalian range. The ORF         exploration confirmed that predicted open reading frames are common but not proof of real genes without further evidence.

  
