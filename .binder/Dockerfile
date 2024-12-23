################################################################################
###                                                                          ###
### Created by Mahdi Manoochehrtayebi                                        ###
###                                                                          ###
### École Polytechnique, Palaiseau, France                                   ###
###                                                                          ###
################################################################################


# Pull the base Docker image from GitHub Container Registry
FROM ghcr.io/ManoochTayebi/Lung-micro-poro-paper-demos:latest

ARG NB_USER=jovyan
ARG NB_UID=1000
USER ${NB_USER}
ENV HOME /home/${NB_USER}
COPY --chown=${NB_UID} . ${HOME}
