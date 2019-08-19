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

  # Software versions
  export R_VERSION=3.5.3

  # use bash as default shell
  echo 'SHELL=/bin/bash' >> /environment

  # make environment file executable
  chmod +x /environment

  # Get dependencies
  apt-get update
  apt-get install -y --no-install-recommends \
    locales

  apt-get install -y --no-install-recommends apt-utils
  apt-get install -y libcairo2
  apt-get install -y libfontconfig1
  apt-get install -y libpango1.0-0
  apt-get install -y libglib2.0-0
  apt-get install -y libpng16-16
  apt-get install -y libpixman-1-0
  apt-get install -y gettext
  apt-get install -y hdf5-tools

  # Configure default locale
  echo "en_US.UTF-8 UTF-8" >> /etc/locale.gen
  locale-gen en_US.utf8
  /usr/sbin/update-locale LANG=en_US.UTF-8
  export LC_ALL=en_US.UTF-8
  export LANG=en_US.UTF-8

  # Install R
  echo "deb http://cran.r-project.org/bin/linux/ubuntu xenial-cran35/" > /etc/apt/sources.list.d/r.list
  apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E084DAB9
  apt-get update
  apt-get install -y gnupg2
  apt-get install -y --no-install-recommends \
    r-base=${R_VERSION}* \
    r-base-core=${R_VERSION}* \
    r-base-dev=${R_VERSION}* \
    r-recommended=${R_VERSION}* \
    r-base-html=${R_VERSION}* \
    r-doc-html=${R_VERSION}* \
    libcurl4-openssl-dev \
    libssl-dev \
    libxml2-dev \
    libcairo2-dev \
    libxt-dev \


  # Add a default CRAN mirror
  echo "options(repos = c(CRAN = 'https://cran.rstudio.com/'), download.file.method = 'libcurl')" >> /usr/lib/R/etc/Rprofile.site

  # Add a directory for host R libraries
  mkdir -p /library
  echo "R_LIBS_SITE=/library:\${R_LIBS_SITE}" >> /usr/lib/R/etc/Renviron.site



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
