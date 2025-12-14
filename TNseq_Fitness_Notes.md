# Tn-Seq and Fitness Analysis – Study Notes

## 1. Concept of Fitness
Fitness is a **relative measure** of the reproductive and survival capacity of an organism (or genotype) in a given environment, compared to other organisms of the same species.  
In genetics, fitness quantifies how much an individual contributes to future generations in terms of genetic material.

Fitness can be seen as the **sum of contributions of individual genes**:
- Some genes contribute **positively** to fitness
- Others contribute **negatively**

Therefore, mutations are not always disadvantageous: removing or altering certain genes can sometimes **increase fitness** under specific conditions.

---

## 2. Transposon Mutagenesis
Transposon mutagenesis is a technique used to generate a large collection of mutants.

- A **transposon** is a DNA element that can insert into the genome.
- When a transposon inserts into a gene, it can **disrupt its function**.
- Transposition is rare, so it is assumed that **only one transposon inserts per cell**.

Each mutant contains a transposon insertion at a different genomic position.

---

## 3. Tn-Seq Experimental Design
In a Tn-Seq experiment:

1. A library of mutants is generated using transposon insertion.
2. Genomic DNA is extracted.
3. Only **transposon–genome junctions** are sequenced.
4. Each junction corresponds to **one mutant**.

The number of sequencing reads at each genomic position reflects the **frequency of that mutant** in the population.

---

## 4. Example: Tryptophan Biosynthesis
Cells are divided into two conditions:
- Medium **with tryptophan (Trp+)**
- Medium **without tryptophan (Trp−)**

Mutants with transposon insertions in genes required for tryptophan biosynthesis:
- Survive in Trp+
- Die or are depleted in Trp−

By comparing insertion profiles between conditions:
- Genes with high insertions in Trp+ and low in Trp− are involved in tryptophan biosynthesis.

Gene essentiality is **condition-dependent** and depends on the growth medium.

---

## 5. Competition Experiment
The experiment can be generalized by sequencing:
- At time **T0**
- After **N generations**

This is called a **competition experiment**.

All mutants grow together, competing with each other.  
Mutants that grow faster increase in frequency, while slower-growing mutants decrease.

- Insertions in essential genes → low frequency at all times
- Insertions that slow growth → decreased frequency
- Insertions that remove unnecessary functions → increased frequency

This defines **gene-specific fitness effects**.

---

## 6. Transposons and Transposition Mechanism
- Transposons exist in many organisms.
- In bacteria, **Insertion Sequences (IS)** encode a transposase enzyme.
- Common transposons (e.g. Tn5, Tn10) carry **antibiotic resistance genes**.

To control insertion:
- The **transposase is provided in trans** (e.g. on a plasmid)
- This prevents the transposon from jumping multiple times

Transposons are introduced by:
- Conjugation
- Transformation

Selection with antibiotics ensures only cells with insertions survive.

---

## 7. Tn-Seq Workflow Summary
Typical steps:
1. Construct a mutant library
2. Grow cells under selective conditions
3. Digest DNA (e.g. with MmeI)
4. PCR amplify transposon junctions
5. Perform Illumina sequencing
6. Map reads to the genome
7. Count insertions and calculate fitness

---

## 8. Fitness Calculation
Fitness is calculated by comparing read counts at two time points.

Main steps:
1. Record reads per insertion at T1 and T2
2. Exclude low-coverage insertions (e.g. <8 reads)
3. Normalize total reads between time points
4. Calculate fitness as the relative growth rate per generation

Fitness values:
- >1 : advantageous
- ≈1 : neutral
- <1 : disadvantageous
- Very low / absent insertions : essential genes

---

## 9. Replication Bias
Fitness values plotted along the genome show a **bias near the origin of replication**.

Reason:
- During replication, some genomic regions are present in **multiple copies**
- This causes overestimation of insertion frequency near the origin

This is not due to multiple insertions, but to **copy number effects**.

Correction methods are needed to remove this bias.

---

## 10. Functional Enrichment
After identifying advantageous and disadvantageous genes, we ask:
- Are certain functional categories overrepresented?

This is tested using **enrichment analysis**:
- Not a random sampling
- Requires statistical models (e.g. hypergeometric distribution)
- More complex than simple binomial models

---

## 11. Case Study: Zika Virus
A variant of transposon mutagenesis uses:
- Very small insertions (15 nt)
- No stop codons

This allows testing which regions of the viral genome:
- Tolerate insertions
- Are essential for replication or immune evasion

---

## Key Takeaways
- Tn-Seq links gene disruption to fitness
- Fitness is condition-dependent
- Competition experiments reveal subtle effects
- Replication bias must be corrected
- Functional enrichment helps biological interpretation
