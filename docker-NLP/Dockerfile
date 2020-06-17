FROM nitinrawat/docker-dl
LABEL maintainer="Nitin Rawat"

# install text augmentation libraries
RUN pip --no-cache-dir install \
		textattack \
		nlpaug \
		python-dotenv \
    nltk>=3.4.5

# widgets is required for progress bar for some of the downloads, specially pretrained embeddings
RUN jupyter labextension install @jupyter-widgets/jupyterlab-manager

# run this command to go the sharedfolder by default. pytorch-gpu image goes to a 'workspace' folder by default
# WORKDIR /

CMD [ "/bin/bash" ]
CMD ["jupyter", "lab", "--port=8888", "--no-browser", "--ip=0.0.0.0", "--allow-root"]
