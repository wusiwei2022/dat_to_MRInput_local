# dat_to_MR_Input_local
dat_to_MRInput_local is a R function to convert a [TwoSampleMR](https://mrcieu.github.io/TwoSampleMR/) object to a [MendelianRandomization](https://cran.r-project.org/web/packages/MendelianRandomization/index.html) object.<br>
This function makes the conversion as the TwoSampleMR::dat_to_MRInput() function does.<br>
With dat_to_MRInput_local, we managed to make this conversion to be a local process.<br>
TwoSampleMR is usually the most used package to process and format GWAS summary data.<br>
Meanwhile, MendelianRandomization package is equipped with some unique fuctions that are not available in TwoSampleMR package.<br>
Particularly, MR approaches applicable to correlated SNPs are only available in MendelianRandomization package.<br>
Therefore, it is sometimes necessary to convert an object from TwoSampleMR format into MendelianRandomization format.

### Significance of the function
Although this function works the same as TwoSampleMR::dat_to_MRInput(), we make it executable locally.<br>
This feature is quite significant when we want to include an LD matrix.<br>
By running the conversion locally, we can calculate the LD matrix with the reference genome in our local machine.<br>
Otherwise, we will have to access the remote server to calculate the LD matrix, which is not always well connected.<br>
In addition, by running the process locally, we can designate the reference genome we want to refer to.<br>
However, the remote server can only use 1000 Genome Project data as the reference.

### Input and output
The input should be a TwoSampleMR object that contains harmonised exposure and outcome data.<br>
The input TwoSampleMR data should be clumperd in reference to the reference genome.<br>
Therefore, all the SNPs in the input file should be available in the reference genome.<br>
The output will be a MendelianRandomization object which can be fed into R functions in MendelianRandomization package. 

### Usage
```r
source("./dat_to_MRInput_local.r")
dat_to_MRInput(dat, get_correlations = FALSE, pop = "EUR", path = NULL)
```
* dat is the harmonised and pre-clumped TwoSampleMR object.<br>
* get_correlations can be set TRUE to include an LD correlation matrix into the output MendelianRandomization object.<br>
* pop is EUR by default, but you should rename it as the filename of reference genome in plink binary format (.bed, .bim, and .fam).<br>
* path is the path to the reference genome file. This parameter must be provided if get_correlations is set TRUE. 
