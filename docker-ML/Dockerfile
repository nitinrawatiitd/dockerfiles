FROM continuumio/anaconda3:latest

# catboost installation steps - https://catboost.ai/docs/installation/python-installation-method-pip-install.html
# pyspark installation - https://pypi.org/project/pyspark/
# h2o installation - https://h2o-release.s3.amazonaws.com/h2o/master/3888/docs-website/h2o-docs/downloading.html
# plotly is required for fbprophet
# requests, tabulate, colorama and future is required for h2o

# conda install nodejs which is required for jupyterlab extensions
RUN conda install nodejs

RUN python3 -m pip install --no-cache-dir --upgrade pip && \
    python3 -m pip install --no-cache-dir \
    npm==0.1.1 \
    jupyterlab==2.1.4 \
    jupyterlab-git==0.20.0 \
    requests==2.22.0 \
    tabulate==0.8.7 \
    "colorama>=0.3.8" \
    future==0.18.2 \
    -f http://h2o-release.s3.amazonaws.com/h2o/latest_stable_Py.html h2o \
    plotly==4.8.1 \
    lightgbm==2.3.1 \
    xgboost==1.1.0 \
    catboost==0.23.2 \
    pyspark==2.4.6 \
    pyomo \
    xarray

# run command to complete installation of jupyterlab-git
RUN jupyter lab build

# install jupyterlab extensions
RUN jupyter labextension install jupyterlab-topbar-extension \
                                 jupyterlab-system-monitor \
                                 jupyterlab-topbar-text \
                                 jupyterlab-logout \
                                 jupyterlab-theme-toggle \
                                 @jupyter-widgets/jupyterlab-manager \
                                 @bokeh/jupyter_bokeh


# doing conda installation for fbprophet as pip install is failing
RUN conda install -c conda-forge fbprophet=0.6

CMD [ "/bin/bash" ]
CMD ["jupyter", "lab", "--port=8888", "--no-browser", "--ip=0.0.0.0", "--allow-root"]
