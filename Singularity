Bootstrap: docker
From: library/julia:1.0.2

%environment
  # use bash as default shell
  SHELL=/bin/bash
  export SHELL

%setup
  # runs on host - the path to the image is $SINGULARITY_ROOTFS

%post

  # load environment variables
  . /environment

  # use bash as default shell
  echo 'SHELL=/bin/bash' >> /environment

  # make environment file executable
  chmod +x /environment

  apt-get update

  apt-get install -y libcairo2
  apt-get install -y libfontconfig1
  apt-get install -y libpango1.0-0
  apt-get install -y libglib2.0-0
  apt-get install -y libpng16-16
  apt-get install -y libpixman-1-0
  apt-get install -y gettext
  apt-get install -y hdf5-tools
  apt-get install -y r-base r-base-dev

  #add julia packages
  /usr/local/julia/bin/julia -e "import Pkg; Pkg.add(\"Distributions\")"
  /usr/local/julia/bin/julia -e "import Pkg; Pkg.add(\"DataFrames\")"
  /usr/local/julia/bin/julia -e "import Pkg; Pkg.add(\"Optim\")"
  /usr/local/julia/bin/julia -e "import Pkg; Pkg.add(\"ArgParse\")"
  /usr/local/julia/bin/julia -e "import Pkg; Pkg.add(\"CSV\")"
  /usr/local/julia/bin/julia -e "import Pkg; Pkg.add(\"Plots\")"
  /usr/local/julia/bin/julia -e "import Pkg; Pkg.add(\"Flux\")"
  /usr/local/julia/bin/julia -e "import Pkg; Pkg.add(\"Revise\")"
  /usr/local/julia/bin/julia -e "import Pkg; Pkg.add(\"CancerSeqSim\")"
  /usr/local/julia/bin/julia -e "import Pkg; Pkg.add(\"ProgressMeter\")"

  # add R packages from CRAN
  Rscript -e "install.packages(pkgs = c('devtools', 'cowplot', 'gtools', 'argparse', 'uwot', 'fuzzyjoin', 'dbscan', 'jcolors', 'ggthemes', 'viridis'), \
      repos='https://cran.revolutionanalytics.com/', \
      dependencies=TRUE, \
      clean = TRUE)"

  #add R packages from bioconductor
   R -e "source('https://bioconductor.org/biocLite.R'); \
                    biocLite('GenomicRanges')"
   R -e "source('https://bioconductor.org/biocLite.R'); \
                     biocLite('IRanges')"

  # add R packages from github
   Rscript -e "library(devtools); install_github('im3sanger/dndscv')"

%runscript
  # executes with the singularity run command
  # delete this section to use existing docker ENTRYPOINT command
  exec /usr/local/julia/bin/julia  "$@"

%test
  # test that script is a success
