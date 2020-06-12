FROM huggingface/transformers-pytorch-gpu

# this will install both nodejs and npm
RUN curl -sL https://deb.nodesource.com/setup_12.x | bash -
RUN apt install -y nodejs

RUN python3 -m pip install --no-cache-dir --upgrade pip && \
    python3 -m pip install --no-cache-dir \
    ipython==7.15.0 \
    jupyterlab==2.1.4 \
    jupyterlab-git==0.20.0

# run command to complete installation of jupyterlab-git
RUN jupyter lab build

# run this command to go the sharedfolder by default. pytorch-gpu image goes to a 'workspace' folder by default
WORKDIR /

CMD [ "/bin/bash" ]
CMD ["jupyter", "lab", "--port=8888", "--no-browser", "--ip=0.0.0.0", "--allow-root"]
