## demoMLexperimentCO

This repository serves as a template to kickstart your ML experiments on Code Ocean and MLflow.

### Clone the repo
(If you have already cloned the repo, you can this section and directly jump to the next section ```Work on Code Ocean```)

To use this template for your ML experiments on Code Ocean, follow the steps below:

**Step 1: Use the Template on GitHub**

1. Click the **Use this template** button located on the top-right corner of the GitHub repository page.
2. Name your repository and configure the settings as needed.
3. This will create a copy of the template repository under your GitHub account.

**Step 2: Clone Repository on Code Ocean**

1. Navigate to Code Ocean and log in to your account.
2. Click the **+** button located on the top-left corner of the dashboard.
3. Select the option to **Clone from VirtualPatientEngine**.
4. Enter the URL to your repository.

**Note:** You are **NOT** required to design test functions for the repos on ML experiments conducted on Code Ocean. However, ensure that your code is well-documented and follows best practices (see the Code/Dev/ML/Data-Ops guide).

For any questions/assistance, please contact Gurdeep.

### Working on Code Ocean


##### 1. Setting up your Code Ocean capsule

1.1 **postInstall Script**: Located in the *environment* folder, the `postInstall` script is where you specify any shareable packages you wish to use for your ML experiments. For the purposes of demo, in this capsule we install the package [demoMLsourceCode repository](https://github.com/VirtualPatientEngine/demoMLsourceCode) from VPE's GitHub page. Please change this script based on your requirements.

1.2 **Jupyter Notebook**: Checkout the `ml_experiment.ipnyb` notebook within the *code* folder, which demonstrates how to import the shareable package specified in the `postInstall` script. Addditionally, it conducts basic ML experiments using the functionalities provided by the imported package. Please change this notebook based on your experiments. Also check out the notebooks `external_ML_model.ipynb` that describes how to import an external model into our MLOps environment, and `register_HF_mocel.ipynb` that describes how to register a Hugging Face model within our MLOps environment.

1.3 **Dockerfile**: Located in the *environment* folder, the `Dockerfile` contains the recipe to load the base image (vscode + copilot + pylint) for your experiment. This is loaded by deafault for your capsule. Should your experiment require another base image, you can select from the available ones by clicking `environment`.


##### 2. Add Credentials (One time process)

You need to attach AWS Cloud Credentials (allows you to connect to AWS) and a Custom Key (path to S3 bucket that contains ml logs) as secrets in the environment of this capsule. This a one time process, and may not be repeated unless there is change in AWS policies or path to the S3 buckets. These credentials must be able to both **Read** and **Write** to a designated S3  bucket. Once you have the credentials and key, follow the steps below:

2.1 Go to the "Account" window and choose "User Secrets." Add "AWS Cloud Credentials" and "Custom Key" (Please check out the MLOps guide to know more about how to set up AWS Cloud Credentials and the DataOps guide on how to set up a Custom Key on Code Ocean or ask Gurdeep).

2.2 Navigate to the "Files" tab and select "environment".

2.3 Attach the appropriate AWS credentials and custom key to the capsule.

##### 3. Launch the Jupyter notebook

3.1 When you are ready, launch a Jupyter Notebook by choosing the icon on top-right.

3.2 Navigate to the notebook that contains your experiment. For the purposes of this demo, you can open `code/ml_experiment.ipynb`.

3.3 Follow the steps described in the notebook to run the ML experiment.

3.4 **Note that the beginning and end of the notebook contain brief code snippets for synchronizing your local copy of the MLflow database with the S3 bucket. The snippet at the start syncs the remote (S3 bucket) to your local copy (`/tmp/mlflow/db`), while the one at the end performs the vice versa operation. Failing to execute these snippets at the correct points (i.e., the start and the end) may result in a loss of synchronization and files.**

<hr>
