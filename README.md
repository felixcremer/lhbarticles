# lhbarticles

These are the premliminary Living Handbook Articles for the NFDI4Earth LHB that are developed in the Measure 2.5.
These are all work in progress.
The final versions will be uploaded to the LHB and available on the NFDI4Earth OneStop4All.

To run the three language quarto notebook we are using Julia as the main process that is used in the jupyter kernel and we use the RCall and PythonCall packages to run R and python code. 

- # Running Quarto with Julia, Python and R
- I am currently working on getting Julia, Python and R running in one quarto notebook.
- I am using Julia to run all languages from one language, because Quarto can only run one Jupyter process at the same time.
- I am using RCall and PythonCall to run R or python code from inside Julia and we use the string macros to hide this fact from the user.
- We are going to use CondaPkg.jl for the installation of all python and R packages that are going to be needed in our notebook.
-
- ## Setting up RCall with CondaPkg
- To let R use CondaPkg to handle the R installation itself and the installation of packages we need to set the R_Home environment variable:
-
-
  ```julia
  - ```
  import CondaPkg
  CondaPkg.add("R")
  ENV["R_HOME"] = CondaPkg.envdir() * "/lib/R"
  import Pkg
  Pkg.build("RCall")
  using RCall
  ```
- ```
- After this setup we can use the pkg repl with the conda command to install shared conda environment
- For example to install the sf R package we use this command in the Julia REPL:
- ] conda add r-sf