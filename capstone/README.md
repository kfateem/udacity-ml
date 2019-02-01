I. Environment setup
--------------------

The are 2 approaches to obtain files:

1. GCP (preferred):

A GCP image, kfateem-capstone-5 is available with the datasets, required libraries and jupyter server and all jupyter notebooks.
The support@udacity.com has image user privliges. Please contact me at karim.fateem@gmail.com if you require additional access.

- to start the image run:

----------------------- BEGIN COMMANDS ------------------------------------

export ZONE="us-west1-b"

export INSTANCE_NAME="alpha-vm"

gcloud compute instances create $INSTANCE_NAME  --zone=$ZONE  --maintenance-policy=TERMINATE  --accelerator="type=nvidia-tesla-v100,count=1"   --metadata="install-nvidia-driver=True" --machine-type=n1-highmem-4 --labels=google-dm=$INSTANCE_NAME --scopes=storage-full,cloud-source-repos --boot-disk-device-name=$INSTANCE_NAME --boot-disk-size=130GB --boot-disk-type=pd-ssd  --network-interface=network=datalab-network  --image=kfateem-capstone-5 --preemptible

gcloud compute ssh --project <ENTER YOUR PROJECT> --zone us-west1-b alpha-vm -- -L 8080:localhost:8080

----------------------- END COMMANDS ------------------------------------

- launch http://localhost:8080/lab?

- navigate to the notebook files from within Jupyter:
~jupyter/github_kfateem_udacity-ml/capstone/notebooks

2. Kaggle:
----------
Datasets are available here https://www.kaggle.com/c/quora-insincere-questions-classification/data
The notebooks are compatible with this docker image: https://github.com/Kaggle/docker-python/blob/master/Dockerfile


II. File summary
----------------

- project.pdf: The capstone project report
- proposal.pdf: The capstone proposal
- notebooks/
          - benchmark.ipynb - notebook for benchmark model
          - capstone.ipynb - notebook for the final model and prediction analysis
          - data_analysis.ipynb - notebook containing dataset analysis
          - benchmak[V2-V5].ipynb -  notebooks containing experimental iterations of the benchmark model
          - capstone[V1-V9].ipynb - notebooks containing experiment iterations of the capstone model. The differences are summarized in the "refinement" section of the report.
          - score_model.ipynb - a notebook to assist with loading models from checkpoints for scoring
