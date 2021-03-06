## CRISPRpred: A flexible and efficient tool for sgRNAs on-target activity prediction in CRISPR/Cas9 systems ##

Necessary Software Tools to install before working with CRISPRpred:
  1. e1071, DAAG, h2o, roxygen2, randomForest, earth and Boruta R packages
      *You can install it by typing 'install.packages('e1071')' in your R console.
  2. viennaRNA tool and set system path accordingly
      *You can download and install it from the following link: http://www.tbi.univie.ac.at/RNA/#source_code_packages

    
#CRISPRpred works in four main steps#

Drawplots folder contains several R scripts to draw interactive plots for dataset. crisprpred folder contains whole structure of crisprpred package. To install this package, follow Step 4.

#Step 1: It constructs features using featurization.R program and Supplementary File1.csv file. You must maintain sample.csv file format.#

    *Open the featurization.R file and set the file name in it or call the functions passing the the above file.

	Your file must be in the same directory as featurization.R file.
    
    *Run featurization.R file and this will generate features accordingly 

	and save it in Supplementary File1.csv file.

#Step 2: Then it runs a wrapper feature selection algorithms of Boruta R package using featureselection.R#

    *Open the featurselection.R file and set the file name as Supplementary File1.csv. 

Your file must be in the same directory as featureselection.R file.

    *Run the featureselection.R file. Some graphs will be generated based on Boruta feature selection algorithm. 

	It generates 'confirmed', 'tentative' and rejected features.

#Step 3: In this step,  it performs anova test to discard irrelevant features.#

    *featureselection.R file also contains the code for anova test. 

So it does that and plot top 30 ranked features. 

These features will be used in machine learning algorithms.
    
#Step 4: It performs machine learning algorithms. We have deployed this as a R package.#

    *Go to crisprpred directory from terminal and run './link.sh'
    *Then run './roxygenize.sh' to generate documentation.
    *Then you can run './check.sh' optionally to check whether everything is ok or not.
    *Then install the package by running './install.sh' in the terminal.

#How to use installed package for prediction:#
    
    *featurelist as vector where last one will be the target. e.g., featurelist = c("X30mer", "Percent.Peptide", "Amino.Acid.Cut.position","predictions")
    Now, suppose we have a file as '../crisprpred/data-raw/sample.csv' and current directory is set to '../crisprpred'
    dir = getwd()
    filepath = paste0(dir,'/data-raw/sample.csv')
    data = read.csv(filepath)
    lmregression(featurelist,data,1)
    
#Citation

Md. Khaledur Rahman and M. Sohel Rahman, "CRISPRpred: A flexible and efficient tool for sgRNAs on-target activity prediction in CRISPR/Cas9 systems", PLoS ONE 12(8): e0181943, August, 2017.

CRISPRpred tool is fully developed by Md. Khaledur Rahman.
If you need any help, please contact: khaled.cse.07@gmail.com
