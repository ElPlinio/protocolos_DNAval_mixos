# Agar Culture of Myxomycetes (Semi-axenic)

**Last updated:** June 2026  
**Reference:** Molina-Viramontes et al. (2025). https://doi.org/10.1111/jeu.70058

---

## Purpose

Semi-axenic cultivation of myxomycete plasmodia from moist chamber sporophores on sterile culture media. This process progressively reduces bacterial contamination, resulting in plasmodia with an altered microbiota (**axenization / dysbiosis state**). Sporophores obtained by this method are referred to as **Axenized Sporocarps (ASp)**.

ASp are the starting material for DNA extraction experiments comparing eubiosis vs. dysbiosis states of the plasmodium microbiome.

---

## Materials

- Petri dishes (90 mm)
- Sterile forceps
- Sterile scalpel
- Stereomicroscope (e.g., OLYMPUS SZX7)
- Autoclave
- Culture media (see below)
- Sterile oat flakes or ground oats (*Avena sativa*)
- Moist Chamber Sporocarps (MCSp) — see [Moist Chamber Culture protocol](moist-chamber-culture.md)

---

## Culture Media

All media are sterilized by autoclaving at **120 °C for 15 min**.

| Abbreviation | Name | Composition |
|---|---|---|
| **WA+** ⭐ | Water Agar + oats | 500 mL distilled water + 7.5 g bacteriological agar. After inoculation, add sterile oat flakes or ground sterile oats. |
| WA | Water Agar | 500 mL distilled water + 7.5 g bacteriological agar |
| OA | Oat Agar | Standard oat agar formulation |
| LA | Litter Agar | Prepared from field litter extract |
| LOA | Litter + Oat Agar | Litter extract + oats |

> ⭐ **WA+ is recommended.** In our hands it produced the best plasmodium growth with the least contaminant growth across all tested media.

---

## Protocol

### Spore Inoculation

1. Under a stereomicroscope, pick individual MCSp using sterile forceps.
2. Crush the sporocarps and inoculate spores onto Petri dishes with sterile culture media.
3. Incubate in **darkness at room temperature (18–22 °C)**.
4. Inspect periodically using back-lit illumination for plasmodium growth.

### Decontamination

5. Once the plasmodium grows, identify uncontaminated sections.
6. Cut sections of clean plasmodium with agar using a sterile scalpel.
7. Transfer to the center of a new Petri dish with the same medium.
8. Repeat until no contaminants are visible in the medium.

### Sporulation Induction

9. Allow the plasmodium to grow without adding further nutrients to induce sporulation under dry, dark conditions.
10. Harvest ASp for molecular analyses.

---

## DNA Extraction (from plasmodia)

Plasmodia should be sampled when they reach at least **5 cm in diameter**. Sample from the growth front (primary and secondary veins) for DNA extraction.

Two extraction approaches have been validated (Molina-Viramontes et al. 2025):

### Commercial method (recommended for diversity studies)
- **Kit:** DNeasy PowerSoil (Qiagen, Germany)
- Follow manufacturer's instructions.
- Recovers higher taxonomic diversity, especially Actinomycetota.
- DNA is stable for up to **2 days** at −20 °C.

### Non-commercial method (recommended for Gram-negative recovery and longer DNA stability)
1. Treat plasmodia with 100 mM EDTA (pH 8) + lysozyme (10 mg/mL) at 37 °C for 1 h.
2. Lyse with SDS and proteinase K at 60 °C.
3. Mechanical disruption with sterile sand and FastPrep homogenizer.
4. Purify by differential precipitation and phenol-chloroform-isoamyl alcohol extraction.
5. Precipitate with polyethylene glycol, wash with ethanol, resuspend in molecular biology-grade water.
6. Add phenol to prevent DNA degradation: extends stability to **>12 days** at −20 °C.
7. Assess purity and integrity by 1% agarose gel electrophoresis. Include reagent blanks.

> ⚠️ Phenol handling requires appropriate fume hood and solvent-disposal infrastructure.

---

## 16S rRNA Amplicon Sequencing

Amplify the V3–V4 hypervariable regions using indexed primers:

| Primer | Sequence (5'→3') |
|--------|-----------------|
| 341F | `CCTACGGGNGGCWGCAG` |
| 805R | `GACTACHVGGGTATCTAATCC` |

- Follow thermal protocol from Montoya-Ciriaco et al. (2020). DOI: [10.1186/s40168-020-0783-6](https://doi.org/10.1186/s40168-020-0783-6)
- Purify triplicate index PCR products from 2% agarose gel.
- Quantify with Quant-iT PicoGreen dsDNA assay (NanoDrop 3300 fluorometer).
- Normalize, pool in equimolar amounts, and sequence on Illumina MiSeq (300 bp paired-end).

---

## Bioinformatics (brief)

| Step | Tool |
|------|------|
| Barcode extraction | QIIME v1.9.1 |
| Quality filtering, denoising, chimera removal | QIIME2 v2023.4 + DADA2 |
| Taxonomic assignment | Scikit-Learn Naive Bayes / GreenGenes2 V3–V4 |
| Contaminant removal | decontam |
| Diversity analysis | R: hillR, vegan, ggplot2, ComplexHeatmap |

Full bioinformatic pipeline: *(add link to scripts repo when available)*

---

## Notes

- Rapid DNA degradation from plasmodia is a known challenge (Shchepin et al. 2017); process immediately after extraction or add phenol.
- Both methods detect dominant taxa consistently; they differ in recovery of low-abundance groups.
- 10-day-old plasmodia from oat agar culture were used for extraction in the reference study.

---

## Citation

> Molina-Viramontes JP, Gómez-Acata ES, Hereira-Pacheco S, Estrada-Torres A, Navarro-Noya YE. (2025). Comparison of Methods to Characterize the Microbiota of Myxomycete Plasmodia. *Journal of Eukaryotic Microbiology*, 73, e70058. https://doi.org/10.1111/jeu.70058
