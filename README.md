# T2T Genomes

This repository tracks the public download links for the assembled genomes, annotations and raw data files of the Publication

**Single-Platform Nanopore Sequencing Enables Diploid Telomere-to-Telomere Genome Assembly and Haplotype-Resolved 3D Chromatin Maps**

Caspar Gross<sup>1, 2,$</sup>, Ramya Pottabulla<sup>1,$</sup>, Fubo Cheng<sup>1</sup>, Sarah Leuchtenberg<sup>1</sup>, Hanna Sophie Hartung<sup>1</sup>, Beate Kristmann<sup>1</sup>, Elena Buena-Atienza<sup>1,3</sup>, Michaela Pogoda<sup>,3</sup>, Nicolas Casadei<sup>1,3</sup>, Stephan Ossowski<sup>1,2\*</sup> and Olaf Riess<sup>1,3\*</sup> 

1 Institute of Medical Genetics and Applied Genomics, University of Tübingen, Tübingen, Germany  
2 Institute for Bioinformatics and Medical Informatics (IBMI), University of Tübingen, Tübingen, Germany  
3 NGS Competence Center Tübingen (NCCT), Tübingen, Germany  
$ These authors contributed equally to the manuscript  

## Publication status:

In submission

## Assemblies

Download link for 24 assemblies (release v1.1): the 23 study samples plus a T2T-ONT assembly of the reference cell line HG002 (`T2T_HG002`).

Assemblies are haplotype-resolved, with contigs assigned to parent of origin where determinable, and use [PanSN-spec](https://github.com/pangenome/PanSN-spec) contig headers (`{sample}#1#contig`, `{sample}#2#contig`, unassigned contigs as `{sample}#0#contig`). Each sample folder contains:

- `{sample}.hap1.fasta` — haplotype 1 (maternal, where determinable)
- `{sample}.hap2.fasta` — haplotype 2 (paternal, where determinable)
- `{sample}.combined.fasta` — both haplotypes plus any unassigned contigs
- `{sample}.contig_pofo_assignment.tsv` — per-contig parent-of-origin assignment table

https://cloud.imgag.de/s/oiHyaeziGCYfD9r

## Annotations

Release v1.1 adds annotation tracks for the 23 study samples (plus a subset for `T2T_HG002`, the reference cell line, which has no Pore-C or methylation data):

- **Phased CpG methylation** — bedMethyl calls per haplotype (`{sample}.hp1.methyl.bed`, `{sample}.hp2.methyl.bed`), from ONT-derived 5mC calls (modkit).
- **Phased 3D chromatin contacts** — per-haplotype and combined contact matrices in mcool format (`{sample}.hp1.mcool`, `{sample}.hp2.mcool`, `{sample}.combined.mcool`), derived from Pore-C data.
- **Small variants** — phased SNVs/indels relative to the diploid assembly (`{sample}.small_variants.vcf.gz`).
- **Structural variants** — haplotype-resolved-assembly-vs-CHM13 structural variant calls (`{sample}.structural_variants.vcf.gz`), from hapdiff/svim-asm.
- **Centromere annotation (CenMap)** — active/complete centromere region calls (`{sample}.complete_cens.bed`, `{sample}.complete_correct_cens.bed`).
- **RepeatMasker annotation** — full RepeatMasker output and a re-annotated, colour-coded BED track (`{sample}.repeatmasker.out`, `{sample}.filtered.bed`, `{sample}.filtered_satellites.bed`). Despite the name, `filtered.bed` applies no length or divergence cutoff (RepeatMasker hits are used as-is; `min_length=0`, `max_div=100`) — "filtered" here means re-classified into repeat class/family with BED9 colour coding, not a quality threshold. `filtered_satellites.bed` is the same set restricted to `Satellite`-class repeats.
- **Assembly issue annotations** — a combined, CHM13-lifted track of potential assembly issues (`{sample}.assembly_issues.lifted.gff3`), backed by the individual Flagger, NucFlag and gap-detection tracks (`{sample}.flagger.bed`, `{sample}.nucflag_status.bed`, `{sample}.nucflag_misasm.bed`, `{sample}.gaps.bed`).

https://cloud.imgag.de/s/oiHyaeziGCYfD9r

## Raw data

Raw sequencing data (basecalled rads) available at GHGA after registration:

https://data.ghga.de/dataset/GHGAD23729013688013

