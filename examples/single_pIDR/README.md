The lines below run simulations of a single IDR in phosphorylated state:

```bash
python prepare.py --name <protein name> --pH <solution pH>
python <protein name>/run.py --path <protein name>
```

where `<protein name>` (10pAsh1 or Ash1) is a protein with sequence provided in the fasta file in the `input` folder. Phosphorylated Ser and Thr are represented as B and O in the fasta file. The charge of pSer and pThr is determined based on the input pH value as detailed in [DOI: 10.1101/2025.03.19.644261](https://doi.org/10.1101/2025.03.19.644261).

### Using the phosphorylation model with CALVADOS 3 (provisional)

`input/residues_pCALVADOS3.csv` contains the CALVADOS 3 residue parameters (identical to `residues_CALVADOS3.csv` in the other examples) plus the pSer (`B`, `SEP`) and pThr (`O`, `TPO`) rows copied unchanged from `residues_pCALVADOS2.csv` (λ = 0.0925 and 0.0013; σ = 0.601 and 0.635 nm).

Note that the pSer/pThr stickiness values were fitted against CALVADOS 2 (Δλ = −0.37 relative to CALVADOS 2 Ser/Thr) and have **not** been re-validated with CALVADOS 3. Applying the same Δλ to the CALVADOS 3 Ser/Thr values would give λ(pSer) = 0.077 and λ(pThr) < 0. To use this file, set `residues_file` in `prepare.py` to `input/residues_pCALVADOS3.csv`; the charges on pSer/pThr are read from the `q` column, so keep the pH-dependent charge update in `prepare.py`.
