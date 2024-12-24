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

# Step 5: Copy the application code to the container (optional)
# COPY . /app

# Step 6: Install Python dependencies (optional, if you have a requirements.txt)
# RUN pip3 install --no-cache-dir -r /app/requirements.txt

# Step 7: Expose a port (e.g., if you're running a web app)
EXPOSE 8000

# Step 8: Set the working directory
WORKDIR /app

# Step 9: Define the default command
CMD ["python3", "app.py"]
