FROM continuumio/anaconda3:latest

# catboost installation steps - https://catboost.ai/docs/installation/python-installation-method-pip-install.html
# pyspark installation - https://pypi.org/project/pyspark/
# h2o installation - https://h2o-release.s3.amazonaws.com/h2o/master/3888/docs-website/h2o-docs/downloading.html
# plotly is required for fbprophet
# requests, tabulate, colorama and future is required for h2o

RUN python3 -m pip install --no-cache-dir --upgrade pip && \
    python3 -m pip install --no-cache-dir \
    jupyterlab \
    requests \
    tabulate \
    "colorama>=0.3.8" \
    future \
    -f http://h2o-release.s3.amazonaws.com/h2o/latest_stable_Py.html h2o \
    plotly==4.8.1 \
    lightgbm \
    xgboost \
    catboost \
    pyspark

# doing conda installation for fbprophet as pip install is failing
RUN conda install -c conda-forge fbprophet

CMD [ "/bin/bash" ]
CMD ["jupyter", "lab", "--port=8888", "--no-browser", "--ip=0.0.0.0", "--allow-root"]

