# PxR3D - Structural-based prediction of protein-RNA photo-crosslinking sites

PxR3D includes two parts: protein-RNA 3D structural feature extraction and crosslinking sites prediction.

# Structural feature extraction
Protein-RNA structural feature extraction mainly uses `3dna2matrix_wrapper.pl`, which depends on DSSR and SNAP of the 3DNA tookit. Please refer to https://x3dna.org for installation details. 

Once installed, specify the directory of 3DNA in `3dna2matirx_wrapper.pl` to run the script. The script requires PDB accession number as input and outputs the features related to amino acids and RNAs in the complex structure. 

`3dna2matrix_wrapper.pl [options] <in.pdb> <out.rna.txt> <out.aa.txt>`

# Crosslinking sites prediction
After extracting the structural features, PxR3D adopts Random Forest to predict crosslinking nucleotides by `PxR3D_nt.R` and crosslinking amino acids by `PxR3D_aa.R `

The two R scripts depend on various functions wrapped in `functions.R` with a list of dependent R packages such as Caret for random foreast prediction. Please install these packages first before running the codes below. 
1. Prediction of crosslinking nucleotides
    
    `Rscript PxR3D_nt.R -v -f test.nt.plot.pdf -i example/featuretable.nt.txt -o test.nt.model.Rds`
2. Prediction of crosslinking amino acids
   
   `Rscript PxR3D_aa.R -v -f test.aa.plot.pdf -i example/featuretable.aa.txt -o test.aa.model.Rds`

Please refer to example folder for the input format of the prediction. 

# Citation
H Feng, XJ Lu, L Liu, D Ustianenko, C Zhang. Structure-based prediction and characterization of photo-crosslinking in native protein-RNA complexes. bioRxiv,  2022.06. 02.494568