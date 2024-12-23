################################################################################
###                                                                          ###
### Created by Mahdi Manoochehrtayebi                                        ###
###                                                                          ###
### École Polytechnique, Palaiseau, France                                   ###
###                                                                          ###
################################################################################


# Pull the base Docker image from GitHub Container Registry
FROM ghcr.io/manoochtayebi/Lung-micro-poro-paper-demos:latest

# Set user configurations if needed
ARG NB_USER=jovyan
ARG NB_UID=1000

# Set home directory for the user
ENV HOME /home/${NB_USER}

# Switch to the correct user
USER ${NB_USER}

# Copy the .repo2docker folder which contains configurations
COPY .repo2docker /home/${NB_USER}/.repo2docker

# Install any necessary system dependencies (example, if you have a apt.txt)
RUN apt-get update && apt-get install -y \
    git \
    curl \
    wget \
    && rm -rf /var/lib/apt/lists/*

# Set up the environment using conda from the environment.yml file
RUN conda env create -f /home/${NB_USER}/.repo2docker/environment.yml \
    && conda clean -a -y

# Activate the environment by default
RUN echo "source activate notebook" >> ~/.bashrc

# Install jupyter-book if needed
RUN pip install jupyter-book

# Expose the Jupyter port
EXPOSE 8888

# Start Jupyter notebook
CMD ["start-notebook.sh"]
