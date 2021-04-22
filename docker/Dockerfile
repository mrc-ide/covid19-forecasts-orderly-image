FROM vimc/orderly.server:master

# Install LaTeX
RUN apt-get update \
        && apt-get install -y --no-install-recommends \
        ghostscript \
        imagemagick \
        lmodern \
        texlive-fonts-recommended \
        texlive-humanities \
        texlive-latex-extra \
        texinfo \
        && apt-get clean \
        && rm -rf /var/lib/apt/lists/ \
        && cd /usr/share/texlive/texmf-dist \
        && wget http://mirrors.ctan.org/install/fonts/inconsolata.tds.zip \
        && unzip inconsolata.tds.zip \
        && rm inconsolata.tds.zip \
        && echo "Map zi4.map" >> /usr/share/texlive/texmf-dist/web2c/updmap.cfg \
        && mktexlsr \
        && updmap-sys

# Install Pandoc
ENV PANDOC_VERSION "2.9.2"
RUN wget https://github.com/jgm/pandoc/releases/download/${PANDOC_VERSION}/pandoc-${PANDOC_VERSION}-1-amd64.deb \
        && dpkg --install pandoc-${PANDOC_VERSION}-1-amd64.deb \
        && rm pandoc-${PANDOC_VERSION}-1-amd64.deb

# system dependencies required to install and run R packages (in
# alphabetical order)
RUN apt-get update && apt-get install -y \
        git \
        libcurl4-openssl-dev \
        libgdal-dev \
        libgit2-dev \
        libgsl0-dev \
        libmagick++-dev \
        libssl-dev \
        libsodium-dev \
        libudunits2-dev \
        libv8-dev \
        libxml2-dev

COPY bin /usr/local/bin/

# Add new packages here (in alphabetical order)
RUN install2.r --error \
        DT \
        EpiEstim \
        Hmisc \
        binom \
        countrycode \
        cowplot \
        dplyr \
        epitrix \
        flexdashboard \
        forcats \
        ggdist \
        ggforce \
        ggnewscale \
        ggplot2 \
        ggpubr \
        ggrepel \
        glue \
        gridExtra \
        incidence \
        janitor \
        patchwork \
        projections \
        purrr \
        rmarkdown \
        sf \
        shiny \
        slider \
        snakecase \
        sp \
        stringr \
        tibble \
        tidyr

## TODO: needed but not found: ascertainr, assessr, weighter

RUN install_packages --repo "https://ncov-ic.github.io/drat" \
  rincewind

WORKDIR /orderly
