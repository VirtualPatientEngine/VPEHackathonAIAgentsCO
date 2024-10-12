---
hide:
  - navigation
  - toc
---

# <font color=black>Setup for AI agents for life sciences</font>
> <font color=black>ℹ️</font><br>
> **Date** 2024-10-14 to -15<br>
> **Location** BioLabs Heidelberg and Online<br>

## Infrastructure and core software
- Cloud infrastructure: [Amazon Web Services](https://aws.amazon.com/de/)
- Computational research platform: [Code Ocean](https://codeocean.com/)
- Version control: [GitHub](https://github.com/VirtualPatientEngine)
- AI Agent application requirements: [Streamlit](https://streamlit.io/), [Ollama](https://ollama.com/), [LangChain](https://www.langchain.com/), and [FAISS](https://github.com/facebookresearch/faiss)

### Step 1: Introduction to our computational research platform with Code Ocean
1. View a [short overview video](https://www.youtube.com/watch?v=k_qddEpTEjo) of the Code Ocean platform
2. Review further information in the Code Ocean [user guide](https://docs.codeocean.com/user-guide) if needed

### Step 2: Enable simultaneous capsule collaboration with version control using git and GitHub
1. Navigate to our [GitHub repository](https://github.com/VirtualPatientEngine/VPEHackathonAIAgentsCO)
2. Each team will create their own fork called "team/name"
3. Each team member will create their own capsule `create a new capsule` through the option `clone from VirtualPatientEngine`
4. After team members update their capsules branch, members should `push` to their teams branch
5. Each team member then updates their capsules with their team members contributions by `pulling` to their capsules branch

> <font color=black>💡tips</font><br>
> 1. Use the command line `terminal` in the VS Code editor for pushing and pulling using `git`<br>
> 2. Quick reference of [git commands](https://www.geeksforgeeks.org/git-cheat-sheet/) if you forget and the [full documentation](https://git-scm.com/docs/git) if typing `git --help` is not sufficient

### Step 3: Familiarization with the template Code Ocean AI Agents capsule
1. README and overview of the repository
2. The Streamlit Application with three starter examples

    > \# setup the chromaDB<br>
    > python /code/embedding_utils.py<br>
    > \# test that we can run the streamlit app<br>
    > python /code/streamlit_app.py<br>
    > \# Run the streamlit app<br>
    > streamlit run /code/streamlit_app.py<br>
    > \# Stop the streamlit app<br>
    > [Ctrl] + [C]

3. Extended examples needed for completing the Hackathon challenges

> <font color=black>💡tips</font><br>
> 1. Use the `Scratch` folder for downloading large data files<br>
> 2. Use the VS Code editor to launch the Ollama server, interact with Streamlit, and code

### Step 4: Launching, working in, and stopping the capsule
1. Click the `VS Code` icon on the top right under `Reproducible run` to launch a cloud workstation on AWS; Please note that the first time you launch a capsule it will take a few minutes to allocate the resources on AWS.
2. Hack away 😀
3. Commit your changes

    > git checkout -b "feat/name"<br>
    > git add .<br>
    > git commit -m "feat: my cool feature"<br>
    > git push origin feat/name<br>

4. Update your branch with your teams changes

    > git fetch --all --prune<br>
    > git merge team/name<br>

5. Share your changes with your teams branch

    > git checkout team/name<br>
    > git pull team/name<br>
    > git merge feat/name<br>
    > git push team/name<br>

6. When you are done, **please shut down the capsule to save resources!** by clicking the `red power` button on the top left.