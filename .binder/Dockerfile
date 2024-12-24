# ################################################################################
# ###                                                                          ###
# ### Created by Mahdi Manoochehrtayebi                                        ###
# ###                                                                          ###
# ### École Polytechnique, Palaiseau, France                                   ###
# ###                                                                          ###
# ################################################################################

# Step 1: Use your custom image from GHCR as the base image
FROM ghcr.io/manoochtayebi/lung-micro-poro-paper-demos:latest

# Step 2: Set the maintainer label
LABEL maintainer="your-email@example.com"

# Step 3: Set environment variables
ENV DEBIAN_FRONTEND=noninteractive

# Step 4: Update the package list and install necessary dependencies
# We will install necessary dependencies without affecting the existing user setup
USER root

RUN apt-get update && apt-get install -y \
    curl \
    wget \
    git \
    python3 \
    python3-pip \
    && rm -rf /var/lib/apt/lists/*

# Step 5: Install Conda (if not already present in the base image)
# If Conda is not available in the base image, you can install Miniconda here
RUN curl -sSL https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh -o miniconda.sh \
    && bash miniconda.sh -b -u \
    && rm miniconda.sh \
    && /root/miniconda3/bin/conda init bash

# Step 6: Clean up and remove any pre-existing 'notebook' environment
RUN /root/miniconda3/bin/conda env remove -n notebook || echo "No existing environment to remove"
RUN /root/miniconda3/bin/conda clean --all -y

# Step 7: Copy the environment.yml file to the container
COPY .repo2docker/environment.yml /tmp/environment.yml

# Step 8: Create Conda environment from environment.yml
RUN /root/miniconda3/bin/conda env create -f /tmp/environment.yml

# Step 9: Expose a port (e.g., if you're running a web app)
EXPOSE 8000

# Step 10: Set the working directory
WORKDIR /app

# Step 11: Set up environment activation (optional)
# If you want to automatically activate the environment, use the entrypoint or CMD
ENTRYPOINT ["/root/miniconda3/bin/conda", "run", "-n", "notebook", "--no-capture-output"]

# Step 12: Define the default command (this is an example command)
CMD ["python3", "app.py"]
