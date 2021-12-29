# example ml flow
MLFlow Docker image configured for Example


Runs mlflow server as the entrypoint.

to test run the docker file from a terminal in the root folder with this command:

docker run -p 5000:5000 nexus-gss.uscis.dhs.gov:1337/argos/vis-argos-mlflow --host 0.0.0.0

Then, navigate to

localhost:5000

to see the tracking UI
