---
hide:
  - navigation
  - toc
---

# <font color=black>Task categories and types for AI agents for life sciences</font>
> <font color=black>ℹ️</font><br>
> **Date** 2024-10-14 to -15<br>
> **Location** BioLabs Heidelberg and Online<br>

- Infrastructure: [Amazon Web Services](https://aws.amazon.com/de/) and [Code Ocean](https://codeocean.com/)
- Application requirements: [Streamlit](https://streamlit.io/), [Ollama](https://ollama.com/), [LangChain](https://www.langchain.com/), and [FAISS](https://github.com/facebookresearch/faiss)

## AI agents for computational modelling and simulation
- Special software requirements: https://github.com/copasi/basico
- Data for computational modelling: ODE mathematical models in SBML format from [BioModels](https://www.ebi.ac.uk/biomodels/) e.g., [insulin dynamics](https://www.ebi.ac.uk/biomodels/BIOMD0000000482)
- Data for model annotation: [cell ontology](https://bioportal.bioontology.org/ontologies/CL), [ChEBI](https://www.ebi.ac.uk/chebi/aboutChebiForward.do), and [UniProtKB](https://www.uniprot.org/)
- Other data: [PubMed](https://pubmed.ncbi.nlm.nih.gov/) for original articles

### Task type 1
- **Description**: Simulation of a mathematical model and reporting of the biomarker trajectories and predicted clinical efficacy
- **Input**: simulation parameters such as initial concentrations
- **Output**: time-course of simulation species

### Task type 2
- **Description**: Creating a mathematical model from scratch
- **Input**: Original article describing the mathematical model and list of equations
- **Output**: SBML model with annotated species

## AI agents for omics and foundation models
- Special software requirements: [scGPT](https://www.nature.com/articles/s41592-024-02201-0)
- Data for analysis: [cell by gene](https://cellxgene.cziscience.com/)
- Other tools/analyses: [differential gene set enrichment analysis using GO](https://amigo.geneontology.org/amigo), UMAP

### Task type 1
- **Description**: Integration of multiple scRNA seq datasets, correction for batch effects, annotation of cells, and reporting of the results as a UMAP
- **Input**: multiple cellxgene datasets for a particular disease (e.g., Rheumatoid Arthritis)
- **Output**: UMAP visualization with cell annotation

### Task type 2
- **Description**: Simulation of gene perturbation and reporting of the predicted differentially expressed genes using pathway enrichment analysis
- **Input**: cell x gene dataset for a particular disease, knockout gene list
- **Output**: list of differentially expressed genes and pathway enrichment analysis visualization

## AI agent for Biomedical knowledge graph reasoning and construction
- Special software requirements: [LLMGraphTransformer](https://api.python.langchain.com/en/latest/graph_transformers/langchain_experimental.graph_transformers.llm.LLMGraphTransformer.html) and [ULTRA](https://github.com/DeepGraphLearning/ULTRA)
- Biomedical knowledge graph dataset: [PrimeKG](https://github.com/mims-harvard/PrimeKG) specifically the subset used in [STARK](https://github.com/snap-stanford/stark)
- Other data: [PubMed](https://pubmed.ncbi.nlm.nih.gov/) for original articles
- Graph database: [NetworkX](https://networkx.org/)

### Task type 1
- **Description**: Knowledge graph Q&A and retrieval of K-hop subgraph explanations
- **Input**: Natural language question (see subset used in https://arxiv.org/abs/2404.13207 for PrimeKG)
- **Output**: Ranked nodes answers and visualization of k-hop subgraphs

### Task type 2
- **Description**: Disease knowledge graph construction from text using a text-to-graph model to construct the initial knowledge graph and link prediction model to fill in gaps in the reconstructed knowledge graph
- **Input**: List of disease MeSH terms and associated articles from PubMed and list of nodes and edges (same as in PrimeKG)
- **Output**: NetworkX representation of the knowledge graph and visualization

### Task type 3
- **Description**: Same as type 1 but including protein embeddings from https://www.uniprot.org/help/embeddings and additional vector similarity search of drug targets embeddings 
- **Input**: Natural language question (see subset used in https://arxiv.org/abs/2404.13207 for PrimeKG)
- **Output**: Ranked nodes answers and visualization of k-hop subgraphs