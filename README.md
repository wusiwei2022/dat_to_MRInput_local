### dat_to_MRInput_local is to convert a TwoSampleMR object to a MendelianRandomization object.
### MendelianRandomization package was equipped with some functions that can be applied on correlated instruments when a correlation matrix is available.
### An important feauture of dat_to_MRInput_local is that it can calculate the LD matrix locally while making the conversion.
### The function is also important when we want to run the conversion many times with the LD matrix calculated. 
# What to input?
### The input should be a TwoSampleMR object that contains harmonised exposure and outcome data.
### The data should be clumperd in reference to the reference genome.
### Therefore all the SNPs in the input file should be available in the reference genome.
