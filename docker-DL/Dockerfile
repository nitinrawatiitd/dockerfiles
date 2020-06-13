FROM nvidia/cuda:10.1-cudnn7-runtime-ubuntu18.04
LABEL maintainer="Nitin Rawat"
## inspired from dockerfiles for huggingface - https://hub.docker.com/r/huggingface/transformers-pytorch-gpu/dockerfile
## and dockerfile from floydhub - https://github.com/floydhub/dl-docker/blob/master/Dockerfile.gpu

RUN apt-get update --fix-missing && \
    apt-get install -y bash \
                   build-essential \
                   git \
                   unzip \
                   vim \
                   wget \
                   curl \
                   ca-certificates \
                   python3 \
                   python3-pip && \
    rm -rf /var/lib/apt/lists

# upgrade pip to latest version. version>19.0 required to install latest version of tensorflow
RUN pip3 install -U pip

# install Tensorflow
RUN pip install --upgrade tensorflow

# Add SNI support to Python
RUN pip --no-cache-dir install \
		pyopenssl \
		ndg-httpsclient \
		pyasn1

# Install useful Python packages using apt-get to avoid version incompatibilities with Tensorflow binary
# especially numpy, scipy, skimage and sklearn (see https://github.com/tensorflow/tensorflow/issues/2034)
RUN pip --no-cache-dir install \
		numpy==1.16.6 \
		scipy \
		nose \
		h5py \
    scikit-learn \
		scikit-image \
		matplotlib \
		pandas \
		sklearn \
		sympy \
    pandas \
    seaborn \
    bokeh \
    gensim \
    networkx

# Install other useful Python packages using pip. Keras is now part of tensorflow
RUN pip --no-cache-dir install --upgrade ipython && \
	pip --no-cache-dir install \
		Cython \
		ipykernel \
		path.py \
    jupyterlab==2.1.4 \
    jupyterlab-git==0.20.0 \
    mkl \
    torch \
    transformers

# this will install both nodejs and npm
RUN curl -sL https://deb.nodesource.com/setup_12.x | bash -
RUN apt install -y nodejs

# run command to complete installation of jupyterlab-git
RUN jupyter lab build

# run this command to go the sharedfolder by default. pytorch-gpu image goes to a 'workspace' folder by default
WORKDIR /

CMD [ "/bin/bash" ]
CMD ["jupyter", "lab", "--port=8888", "--no-browser", "--ip=0.0.0.0", "--allow-root"]
