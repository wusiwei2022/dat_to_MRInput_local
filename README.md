# dat_to_MR_Input_local
dat_to_MRInput_local is a R function to convert a [TwoSampleMR](https://mrcieu.github.io/TwoSampleMR/) object to a [MendelianRandomization](https://cran.r-project.org/web/packages/MendelianRandomization/index.html) object. This function makes the conversion as the TwoSampleMR::dat_to_MRInput() function does.<br>  

## Background
TwoSampleMR is usually the most used package to process and format GWAS summary data. However, MendelianRandomization package is also equipped with some unique fuctions that are not available in TwoSampleMR package. Particularly, MR methods on correlated SNPs are only available in MendelianRandomization package. Therefore, it is necessary to convert an object from TwoSampleMR format into MendelianRandomization format.<br>  
Althougn TwoSampleMR::dat_to_MRInput() can convert data from TwoSampleMR format to MendelianRandomization format, the process is run by accessing the remote server. We are committed to make the conversion in our local machine with this function.

## Significance of the function
* By running the conversion locally, we can calculate the LD matrix with the reference genome in our local machine. Otherwise, we will have to access the remote server to calculate the LD matrix, which is not always well connected.<br>  
* In addition, by running the process locally, we can designate the reference genome we want to refer to. On the contrary, the remote server only use 1000 Genome Project data as the reference.

## Input and output
* The input should be a TwoSampleMR object that contains harmonised exposure and outcome data. It should be clumperd in reference to the reference genome. Therefore, all the SNPs in the input file should be available in the reference genome.<br>  
* The output will be a MendelianRandomization object which can be fed into R functions in MendelianRandomization package. 

## Usage
```r
source_url("https://raw.githubusercontent.com/wusiwei2022/dat_to_MRInput_local/refs/heads/master/Codes_dat_to_MRInput_local.R")
dat_to_MRInput(dat, get_correlations = FALSE, pop = "EUR", path = NULL)
```
* dat: the harmonised and pre-clumped TwoSampleMR object.<br>
* get_correlations: TRUE if we need to include an LD correlation matrix into the output MendelianRandomization object.<br>
* pop: EUR by default, but should be named as the filename of reference genome in plink binary format (.bed, .bim, and .fam).<br> 
* path: the path to the reference genome file, and must be provided if get_correlations is TRUE. 

## Citation
Please cite this R function using the link: [https://github.com/wusiwei2022/dat_to_MRInput_local](https://github.com/wusiwei2022/dat_to_MRInput_local)
