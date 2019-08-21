Bootstrap: docker
From: jupyter/datascience-notebook

  # add R packages from CRAN
  Rscript -e "install.packages(pkgs = c('devtools', 'ggplot2', 'dplyr', 'tidyr', 'stringr', 'cowplot', 'gtools', 'argparse','jcolors', 'ggthemes', 'viridis', 'forcats', 'Hmisc', 'readr', 'ggridges', 'readxl', 'purrr'), \
      repos='https://cran.revolutionanalytics.com/', \
      dependencies=TRUE, \
      clean = TRUE)"

  #add R packages from bioconductor
   R -e "source('https://bioconductor.org/biocLite.R'); \
                    biocLite('GenomicRanges')"
   R -e "source('https://bioconductor.org/biocLite.R'); \
                     biocLite('IRanges')"
   R -e "source('https://bioconductor.org/biocLite.R'); \
                     biocLite('Biostrings')"
   R -e "source('https://bioconductor.org/biocLite.R'); \
                    biocLite('Rsamtools')"
   R -e "source('https://bioconductor.org/biocLite.R'); \
                    biocLite('seqinr')"
   R -e "source('https://bioconductor.org/biocLite.R'); \
                    biocLite('rtracklayer')"
   R -e "source('https://bioconductor.org/biocLite.R'); \
                    biocLite('TCGAbiolinks')"

  # add R packages from github
   Rscript -e "library(devtools); install_github('im3sanger/dndscv')"

  #add julia packages
  /usr/local/julia/bin/julia -e "import Pkg; Pkg.add(\"Distributions\")"
  /usr/local/julia/bin/julia -e "import Pkg; Pkg.add(\"DataFrames\")"
  /usr/local/julia/bin/julia -e "import Pkg; Pkg.add(\"Optim\")"
  /usr/local/julia/bin/julia -e "import Pkg; Pkg.add(\"ArgParse\")"
  /usr/local/julia/bin/julia -e "import Pkg; Pkg.add(\"Distances\")"
  /usr/local/julia/bin/julia -e "import Pkg; Pkg.add(\"CSV\")"
  /usr/local/julia/bin/julia -e "import Pkg; Pkg.add(\"Plots\")"
  /usr/local/julia/bin/julia -e "import Pkg; Pkg.add(\"Flux\")"
  /usr/local/julia/bin/julia -e "import Pkg; Pkg.add(\"Revise\")"
  /usr/local/julia/bin/julia -e "import Pkg; Pkg.add(\"StatsBase\")"
  /usr/local/julia/bin/julia -e "import Pkg; Pkg.add(\"LinearAlgebra\")"
  /usr/local/julia/bin/julia -e "import Pkg; Pkg.add(\"ProgressMeter\")"
  /usr/local/julia/bin/julia -e "import Pkg; Pkg.add(\"NLSolversBase\")"
  /usr/local/julia/bin/julia -e "import Pkg; Pkg.clone(\"https://github.com/marcjwilliams1/StemCellModels.jl\")"
  /usr/local/julia/bin/julia -e "import Pkg; Pkg.clone(\"https://github.com/marcjwilliams1/CancerSeqSim.jl\")"
  /usr/local/julia/bin/julia -e "import Pkg; Pkg.add(\"RCall\")"
