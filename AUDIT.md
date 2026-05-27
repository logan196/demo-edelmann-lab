# Demo Accuracy Audit — Edelmann Lab × Novaflow

## Sources checked
- Cancer Res 2021, PMID:34003775 (PMC8318201) — full text + Tables 1 & 2
- GEO GSE153385 (ISC mRNA-seq, 18 mouse samples)
- GEO GSE183747 (Msh2/Tgfbr2 colon tumor microarray, 12 arrays)
- Tosti et al. CMGH 2022 PMID:35688320
- Tosti, Srivastava & Edelmann, Cancer Prev Res 2023 PMID:37012205

## MAJOR ISSUES (fabricated data)

### 1. NES values for pathways are INVENTED
- Demo shows NES +2.1, +1.9, +1.7, +1.6, −1.8, −1.5
- Paper Fig 3A shows a bubble chart but does NOT list specific NES values in text
- **Fix:** Remove NES numbers, label as "enriched (↑)" or "depleted (↓)" only

### 2. "Tumor (GSE183747)" column in Table 1 cross-reference is FABRICATED
- Demo claims specific genes as "↑ confirmed" or "NS" in GSE183747 tumors
- We never analyzed GSE183747 and no published paper reports which Table 1 genes are DE in that dataset
- **Fix:** Remove the tumor column, or mark it clearly as "analysis pending"

### 3. "8 are also upregulated" claim is fabricated
- Derived from the fabricated tumor column above
- **Fix:** Remove this specific count

### 4. AI Response #3 — classification result is FABRICATED
- Claims "correctly separates all 6 tumor from 6 mucosa" using the 41-gene classifier
- This analysis was never run. Paper validated the 41 genes in human LS vs FAP, not in GSE183747 mouse tumors
- **Fix:** Show this as a proposed analysis (pipeline "running"), not a completed result

### 5. End-to-end validation summary is UNVERIFIED
- The ISC→Patient link is real (from the paper). The ISC→Tumor link (GSE183747) was never tested
- **Fix:** Show the verified link (ISC→Patient) and the proposed one (ISC→Tumor) distinctly

## MODERATE ISSUES

### 6. Gene table mixes Table 1, Table 2, and qRT-PCR data
- Header says "top genes from Table 2" but includes:
  - Nr1h5 (Table 1, not Table 2 KO-specific signature)
  - Nlrp9b (Table 1, not Table 2)
  - Lgr5, Ascl2, Olfm4 (qRT-PCR validation from Fig 2D, not in any table)
- **Fix:** Split into clear sections or relabel

### 7. Tosti, Srivastava & Edelmann 2023 mischaracterized
- Described as showing "same stem cell program carries through to tumors"
- Actually: a review titled "Vaccination and microbiota manipulation approaches for colon cancer prevention in rodent models"
- **Fix:** Correct the citation context

### 8. Muc6 labeled "Premature differentiation marker"
- Paper doesn't call Muc6 a differentiation marker. Muc2 is the goblet marker mentioned
- Muc6 is actually a gastric mucin gene
- **Fix:** Change label to "Gastric mucin" or just "Mucin gene"

## MINOR ISSUES

### 9. "Microbiota 16S (Tosti 2022)" in sidebar
- Tosti 2022 CMGH paper is about microbiota-dependent carcinogenesis (germ-free vs conventional)
- May not have done 16S sequencing specifically
- **Fix:** Change to "Microbiota & CRC (Tosti 2022)"

### 10. Nr1h5 note says "Dose-dependent with Msh2 alleles"
- Nr1h5 IS in Table 1 (dose-dependent), but it should be in the Table 1 section, not Table 2
- This note is accurate for the gene, just misplaced in the table

## VERIFIED CORRECT ✅
- GSE153385 accession and sample counts (18 samples, 119 mice)
- Illumina HiSeq4000
- 340 DEGs (284 up, 56 down) for Msh2-KO vs WT Lgr5+ ISC
- 48 unique MMRd ISC signature genes (Table 2)
- All fold changes from Table 1 and Table 2 (checked each against paper values)
- All log₂FC calculations (verified mathematically)
- Car1 21× at protein level
- Spp1 only in Lgr5+ at protein level
- Spp1 IHC co-localization with LGR5
- Pathway names (Integrin, Focal Adhesion, Inflammatory Response, Wnt↓, Ribosomes↓)
- 41/197 signature genes validated in human LS
- GSE183747: 12 arrays, Affymetrix Mouse Gene 2.0 ST, contact = Elena Tosti
- Wang et al. 2022 NAR (Exo1-D173A)
