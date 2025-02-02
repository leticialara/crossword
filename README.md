# crossword
A data-driven simulation language for the design of genetic-mapping experiments and breeding strategies

Crossword utilizes the widely available results of next-generation sequencing data to create more realistic simulations and to simplify user input. The software was written in R, but simulations are defined in a simplified language that is converted to R prior to running. A graphical user interface is available to facilitate your simulation description.

## Installation:
0. Open a command prompt and run R by typing "R[enter]".  Unless otherwise indicated, the following commands should be typed at the R prompt. "devtools" is required to install any package from github. If you do not have it, it can be installed by the following command:

        install.packages("devtools")

1. If simcross is not installed, we suggest to install it in advance.  
    
        devtools::install_github("kbroman/simcross",force=TRUE)

2. Install crossword:        
    
        devtools::install_github("USDA-ARS-GBRU/crossword")
3. Automated test suite: the following commands can be run to test library loading and crossword commands since "crossword_script_input_file.script" has examples of all crossword syntax commands
         
          library('crossword')
          script_file = paste0(system.file("extdata",package="crossword"),"/crossword_script_input_file.script")
          run_pipeline(script_file)
          
*NOTE: Different example scripts and input files, which were used in the manuscript, are available in "paper_simulations" directory.

## Running crossword:

The full manual is available at Wiki page in the tab above.

### The original xwindow GUI implementation of crossword is being moved to a shiny interface and is currently unusable
### ~~For running using GUI:~~  
~~The x-window environment should open and commands can be entered accordingly.~~

### For running directly from crossword script:
  
          library('crossword')
          script_file = paste0(system.file("extdata",package="crossword"),"/crossword_script_input_file.script")
          run_pipeline(script_file)

### For running multiple simulations using a range of parameters:

See the listOfParameters.txt example file.  The variable names in listOfParameters.txt should match those use in the crossword script.  We recommend using all-caps for these names in order to be clear.

          script_file2 = paste0(system.file("extdata",package="crossword"),"/test2.script")
          list = paste0(system.file("extdata",package="crossword"),"/listOfParameters.txt")
          run_batch(script_file2,list2,run=TRUE)

### For running using Rscript (outside R):

These commands are run at the command prompt (not in R, as the above).  Copy "crossword.R" and the script file from the installed library to the local location and modify as needed.
          
          Rscript ./crossword.R tutorial
          Rscript ./crossword.R crossword_script_input_file.script

Auxiliary functions can be run through Rscript by passing the function name then the function's arguments in their order.
            
            Rscript ./crossword.R vcf2hapmap peanut.vcf peanut.hapmap

## Citation: 
Korani W, Vaughn JN. Crossword: A data-driven simulation language for the design of genetic-mapping experiments and breeding strategies. Scientific Reports. 2019;9: 4386.

https://www.nature.com/articles/s41598-018-38348-y


| External Resource  | Reference | Licence |
| ------------- | ------------- | ------------- | 
| simcross | http://kbroman.org/simcross/ https://kbroman.org/simcross/assets/vignettes/simcross.html | Open_Source | 
| rrBLUP |Endelman, J. B. 2011. Ridge Regression and Other Kernels for Genomic Selection with R Package rrBLUP. Plant Genome 4:250-255 | Open_Source | 
| ART | Weichun Huang, Leping Li, Jason R Myers, and Gabor T Marth. ART: a next-generation sequencing read simulator, Bioinformatics (2012) 28 (4): 593-594 | Open_Source | 
