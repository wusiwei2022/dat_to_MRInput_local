# dat_to_MR_Input_local
dat_to_MRInput_local is a R function to convert a TwoSampleMR object to a MendelianRandomization object.
This function makes the conversion as the TwoSampleMR::dat_to_MRInput() function does.
With dat_to_MRInput_local, we managed to make this conversion to be a local process. 
TwoSampleMR is usually the most used package to process and format GWAS summary data.
Meanwhile, MendelianRandomization package is equipped with some unique fuctions that are not available in TwoSampleMR package.
Particularly, MR approaches applicable to correlated SNPs are only available in MendelianRandomization package.
Therefore, it is sometimes necessary to convert an object from TwoSampleMR format into MendelianRandomization format.

### Significance of the function
Although this function works the same as TwoSampleMR::dat_to_MRInput(), we make it executable locally.
This feature is quite significant when we want to include an LD matrix.
By running the conversion locally, we can calculate the LD matrix with the reference genome in our local machine.
Otherwise, we will have to access the remote server to calculate the LD matrix, which is not always well connected.
In addition, by running the process locally, we can designate the reference genome we want to refer to.
However, the remote server can only use 1000 Genome Project data as the reference.

### Input and output
The input should be a TwoSampleMR object that contains harmonised exposure and outcome data.
The input TwoSampleMR data should be clumperd in reference to the reference genome.
Therefore, all the SNPs in the input file should be available in the reference genome.
The output will be a MendelianRandomization object which can be fed into R functions in MendelianRandomization package. 
