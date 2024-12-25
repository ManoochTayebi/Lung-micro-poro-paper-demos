# ################################################################################
# ###                                                                          ###
# ### Created by Mahdi Manoochehrtayebi                                        ###
# ###                                                                          ###
# ### École Polytechnique, Palaiseau, France                                   ###
# ###                                                                          ###
# ################################################################################

# Step 1: Use your custom image from GHCR as the base image
FROM ghcr.io/manoochtayebi/lung-micro-poro-paper-demos:latest

ARG NB_USER=jovyan
ARG NB_UID=1000
USER ${NB_USER}
ENV HOME /home/${NB_USER}
COPY --chown=${NB_UID} . ${HOME}
