# ################################################################################
# ###                                                                          ###
# ### Created by Mahdi Manoochehrtayebi                                        ###
# ###                                                                          ###
# ### École Polytechnique, Palaiseau, France                                   ###
# ###                                                                          ###
# ################################################################################


# # Pull the base Docker image from GitHub Container Registry
# FROM ghcr.io/manoochtayebi/lung-micro-poro-paper-demos:latest

# # Set user configurations if needed
# ARG NB_USER=jovyan
# ARG NB_UID=1000

# # Set home directory for the user
# ENV HOME /home/${NB_USER}

# # Switch to the correct user
# USER ${NB_USER}

# # Copy the .repo2docker folder which contains configurations
# COPY .repo2docker /home/${NB_USER}/.repo2docker

# # Install any necessary system dependencies (example, if you have a apt.txt)
# RUN apt-get update && apt-get install -y \
#     git \
#     curl \
#     wget \
#     && rm -rf /var/lib/apt/lists/*

# # Set up the environment using conda from the environment.yml file
# RUN conda env create -f /home/${NB_USER}/.repo2docker/environment.yml \
#     && conda clean -a -y

# # Activate the environment by default
# RUN echo "source activate notebook" >> ~/.bashrc

# # Install jupyter-book if needed
# RUN pip install jupyter-book

# # Expose the Jupyter port
# EXPOSE 8888

# # Start Jupyter notebook
# CMD ["start-notebook.sh"]



# Step 1: Set a base image
FROM ubuntu:20.04

# Step 2: Set the maintainer label
LABEL maintainer="your-email@example.com"

# Step 3: Set environment variables
ENV DEBIAN_FRONTEND=noninteractive

# Step 4: Update the package list and install any necessary dependencies
RUN apt-get update && apt-get install -y \
    curl \
    wget \
    git \
    python3 \
    python3-pip \
    && rm -rf /var/lib/apt/lists/*

# Step 5: Copy the application code to the container (optional)
# If you have an app to copy, you would do something like:
# COPY . /app

# Step 6: Install Python dependencies (optional, if you have a requirements.txt)
# RUN pip3 install --no-cache-dir -r /app/requirements.txt

# Step 7: Expose a port (e.g., if you're running a web app)
EXPOSE 8000

# Step 8: Set the working directory
WORKDIR /app

# Step 9: Define the default command (this will run when the container starts)
CMD ["python3", "app.py"]
