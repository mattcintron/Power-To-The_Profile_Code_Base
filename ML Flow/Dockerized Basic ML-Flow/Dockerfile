#FROM python:3.7.0
FROM python:3

LABEL maintainer "Daniel van der Ende <daniel.vanderende@gmail.com>"

RUN mkdir /mlflow/

#new stuff
#RUN apt-get install gfortran libopenblas-dev liblapack-dev
#RUN pip install scipy
#RUN pip install -U scikit-learn
RUN pip install mlflow

#RUN pip install mlflow==0.8.0

EXPOSE 5000

CMD mlflow server --host 0.0.0.0 --workers 2 --artifacts-destination /mlflow

