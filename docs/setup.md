---
hide:
  - navigation
  - toc
---

# <font color=black>Setup for AI agents for life sciences</font>

## Infrastructure and core software
- Cloud infrastructure: [Amazon Web Services](https://aws.amazon.com/de/)
- Computational research platform: [Code Ocean](https://codeocean.com/)
- Version control: [GitHub](https://github.com/VirtualPatientEngine)
- AI Agent application requirements: [Streamlit](https://streamlit.io/), [Ollama](https://ollama.com/), [LangChain](https://www.langchain.com/), and [FAISS](https://github.com/facebookresearch/faiss)

## Setup
### Step 1: Introduction to our computational research platform with Code Ocean
1. View a [short overview video](https://www.youtube.com/watch?v=k_qddEpTEjo) of the Code Ocean platform
2. Review further information in the Code Ocean [user guide](https://docs.codeocean.com/user-guide) if needed

### Step 2: Enable simultaneous capsule collaboration with version control using git and GitHub
1. Navigate to our [GitHub repository](https://github.com/VirtualPatientEngine/VPEHackathonAIAgentsCOTemplate)
2. Each team will have their own branch `[Team Name]` created by the coaches

    VPEHackathonAIAgentsCOTemplate/main -> VPEHackathonAIAgentsCOTemplate/[Team Name]

3. Each team member will need to add their own pesonal access token in Code Ocean

    1. Follow GitHub instructions to generate a personal access token: https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens
    2. Save your personal access token! You will also need it when working with Git
    3. Then on Code Ocean, click on the `account` icon on the bottom left side, and go to `credentials`.
    4. Click on `⊕ Add credential` and choose `GitHub`, then add your username (in GitHub) and the token you have created.

4. Each team member will create their own capsule in Code Ocean by cloning the template repository

    1. Click on the `New Capsule` button on the top right corner.
    2. Select `Copy from public Git`.
    3. Paste the git repository address: (i.e., https://github.com/VirtualPatientEngine/VPEHackathonAIAgentsCOTemplate)
    4. Click `clone`
    5. The capsule will be cloned within a few seconds.

5. Each team member will need to attach shared data assets to their own capsule in Code Ocean

    1. In the capsule view, in the data folder in the files tree click ⚙️manage
    2. Attach the data-assets by clicking the plus sign (⊕)
    3. The data assets are `collections: cellxgene census metadata 2024-04-24` and `ollama_models_09_2024`

6. Individual team members will contribute by syncing with their teams branch (see section step 4 below)

> <font color=black>💡Tip</font><br>
> 1. Use the command line `terminal` in the VS Code editor for running `git` commands<br>
> 2. Quick reference of [git commands](https://education.github.com/git-cheat-sheet-education.pdf) if you forget and the [full documentation](https://git-scm.com/docs/git) if typing `git --help` is not sufficient<br>

### Step 3: Familiarization with the template Code Ocean AI Agents capsule
1. README and overview of the repository
2. The Streamlit Application with three starter examples

    > \# test that we can run the streamlit app<br>
    > python /code/streamlit_app.py<br>
    > \# Run the streamlit app<br>
    > streamlit run /code/streamlit_app.py<br>
    > \# Stop the streamlit app<br>
    > [Ctrl] + [C]<br>

3. Extended examples needed for completing the Hackathon challenges
4. Downloading datasets and models (Ollama example)

    > \# Create the source directory if it doesn't exist<br>
    > mkdir -p /scratch/.ollama<br>
    > \# delete the existing symbolic link link<br>
    > rm /root/.ollama<br>
    > \# Create the new symbolic link (each write to /root/.ollama will be directed to /scratch/.ollama)<br>
    > ln -s  /scratch/.ollama /root/.ollama<br>
    > \# copy the key:<br>
    > cp /data/.ollama/id_ed25519 /scratch/.ollama/id_ed25519<br>
    > \# start the ollama server in the scratch directory<br>
    > cd scratch<br>
    > cd ollama serve<br>
    > \# list and pull models<br>
    > ollama list<br>
    > ollama pull llama3.1<br>

5. Downloading datasets and models (Stark example)

    > \# Create and activate a virtual environment (Optional since we are working in a docker container)<br>
    > python -m venv .venv<br>
    > source .venv/bin/activate<br>
    > \# Install stark via pip<br>
    > pip install stark-qa<br>
    > \# Download to scratch<br>
    > python<br>
    > from stark_qa import load_skb<br>
    > skb = load_skb("prime", download_processed=True, root="/scratch")<br>
    > \# Deactivate virtual environment when done<br>
    > exit()<br>
    > deactivate<br>

> <font color=black>💡Tip</font><br>
> 1. Use the `Scratch` folder for downloading large data files<br>
> 2. Use the VS Code editor to launch the Ollama server, interact with Streamlit, coding, etc.<br>
> 3. If you use a virtual envrionment, be sure to add the virtual environment directory to `.gitignore`!<br>
> 4. Ollama [cheat sheat](https://secretdatascientist.com/ollama-cheatsheet/)<br>

### Step 4: Launching, working in, and stopping the capsule
1. Click the `VS Code` icon on the top right under `Reproducible run` to launch a cloud workstation on AWS; Please note that the first time you launch a capsule it will take a few minutes to allocate the resources on AWS.
2. In a new terminal, add the remote team branches

    > \# add a the VPE remote branches with your teams branch<br>
    > git remote -v<br>
    > git remote add upstream https://[user name]:[token]@github.com/VirtualPatientEngine/VPEHackathonAIAgentsCOTemplate.git<br>
    > git fetch --all --prune<br>

2. Check to see that your teams branch is there e.g., `upstream [Team Name]`. This is the branch that your team will sync with
3. Create your branch derived from your teams branch

    > \# check to see that your teams branch is there<br>
    > git branch -v<br>
    > \# switch to your teams branch<br>
    > git checkout [Team Name]
    > \# create a branch **starting from your teams branch** for your features (feat) and fixes (fix)<br>
    > git checkout -b [feat or fix]/[name]<br>

3. Hack away 😀
4. Commit your changes

    > \# stage your changes for the next commit<br>
    > git add .<br>
    > \# add your changes to the commit<br>
    > git commit -m "feat: my cool feature"<br>
    > \# push your changes to your local branch<br>
    > git push origin [feat or fix]/[name]<br>

5. Update your branch with your teams changes

    > \# fetch all changes from upstream branches<br>
    > git fetch --all --prune<br>
    > \# update the local team branch<br>
    > git checkout [Team Name]<br>
    > git pull [Team name]<br>
    > \# merge changes from your local team branch into your branch<br>
    > git checkout [feat or fix]/[name]<br>
    > git merge [Team Name]<br>

6. Share your changes with your teams branch

    > \# ensure your local team branch is up to date<br>
    > git checkout [Team Name]<br>
    > git fetch --all --prune<br>
    > git pull [Team name]<br>
    > \# merge your changes (and resolve any conflicts)<br>
    > git merge [feat or fix]/[name]<br>
    > git push upstream [Team Name]<br>
    > \# delete your old branch and begin a new one<br>
    > git branch -D [feat or fix]/[name]<br>
    > git checkout -b [feat or fix]/[name]<br>

7. When you are done, **please shut down the capsule to save resources!** by clicking the `red power` button on the top left.