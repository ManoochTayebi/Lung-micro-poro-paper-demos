################################################################################
###                                                                          ###
### Created by Martin Genet                                                  ###
###                                                                          ###
### École Polytechnique, Palaiseau, France                                   ###
###                                                                          ###
################################################################################

FROM jupyter/scipy-notebook:latest

# Copy repo into the image, cf. https://mybinder.readthedocs.io/en/latest/tutorials/dockerfile.html.
ARG NB_USER=jovyan
ARG NB_UID=1000
USER ${NB_USER}
ENV HOME /home/${NB_USER}
COPY --chown=${NB_UID} . ${HOME}
