# ################################################################################
# ###                                                                          ###
# ### Created by Mahdi Manoochehrtayebi                                        ###
# ###                                                                          ###
# ### École Polytechnique, Palaiseau, France                                   ###
# ###                                                                          ###
# ################################################################################

# Step 1: Use your custom image from GHCR as the base image
FROM ghcr.io/manoochtayebi/lung-micro-poro-paper-demos:latest

# Set build arguments and environment variables
ARG NB_USER=jovyan
ARG NB_UID=1000
ENV HOME=/home/${NB_USER}
USER ${NB_USER}

# Set the working directory
WORKDIR ${HOME}

# Copy the repository content to the image
COPY --chown=${NB_UID} . ${HOME}

# Install APT packages from .repo2docker/apt.txt
USER root
RUN apt-get update && \
    apt-get install -y --no-install-recommends $(cat .repo2docker/apt.txt | xargs) && \
    apt-get clean && rm -rf /var/lib/apt/lists/*

# Install Conda and Python dependencies from .repo2docker/environment.yml
RUN apt-get update && \
    apt-get install -y --no-install-recommends python3 python3-pip && \
    pip install --no-cache-dir conda && \
    conda env update -f .repo2docker/environment.yml && \
    conda clean --all -y

# Switch back to jovyan user
USER ${NB_USER}
