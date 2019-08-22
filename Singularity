Bootstrap: docker
From: jupyter/datascience-notebook


  # add R packages from CRAN
  Rscript -e "install.packages(pkgs = c('devtools', 'ggplot2', 'dplyr', 'tidyr', 'stringr', 'cowplot', 'gtools', 'argparse','jcolors', 'ggthemes', 'viridis', 'forcats', 'Hmisc', 'readr', 'ggridges', 'readxl', 'purrr'), \
      repos='https://cran.revolutionanalytics.com/', \
      dependencies=TRUE, \
      clean = TRUE)"

  #add R packages from bioconductor
   Rscript -e "install.packages('BiocManager')"
   Rscript -e "BiocManager::install('GenomicRanges')"
   Rscript -e "BiocManager::install('IRanges')"
   Rscript -e "BiocManager::install('Biostrings')"
   Rscript -e "BiocManager::install('Rsamtools')"
   Rscript -e "BiocManager::install('seqinr')"
   Rscript -e "BiocManager::install('rtracklayer')"
   Rscript -e "BiocManager::install('TCGAbiolinks')"

  # add R packages from github
   Rscript -e "library(devtools); install_github('im3sanger/dndscv')"

  #add julia packages
  julia -e "import Pkg; Pkg.add(\"Distributions\")"
  julia -e "import Pkg; Pkg.add(\"DataFrames\")"
  julia -e "import Pkg; Pkg.add(\"Optim\")"
  julia -e "import Pkg; Pkg.add(\"ArgParse\")"
  julia -e "import Pkg; Pkg.add(\"Distances\")"
  julia -e "import Pkg; Pkg.add(\"CSV\")"
  julia -e "import Pkg; Pkg.add(\"Plots\")"
  julia -e "import Pkg; Pkg.add(\"Flux\")"
  julia -e "import Pkg; Pkg.add(\"Revise\")"
  julia -e "import Pkg; Pkg.add(\"StatsBase\")"
  julia -e "import Pkg; Pkg.add(\"LinearAlgebra\")"
  julia -e "import Pkg; Pkg.add(\"ProgressMeter\")"
  julia -e "import Pkg; Pkg.add(\"NLSolversBase\")"
  julia -e "import Pkg; Pkg.clone(\"https://github.com/marcjwilliams1/StemCellModels.jl\")"
  julia -e "import Pkg; Pkg.clone(\"https://github.com/marcjwilliams1/CancerSeqSim.jl\")"
  julia -e "import Pkg; Pkg.add(\"RCall\")
