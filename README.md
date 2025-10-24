# Personality Knowledge Graph Challenge
This project was developed for the LLM Reasoning & Personality Knowledge Graph Challenge. It demonstrates how large language models (LLMs) can be used to extract structured knowledge and infer personality traits from unstructured text data. The final output is an interpretable Personality Knowledge Graph that connects people, organizations, skills, and inferred traits.

## Overview
The goal of this project is to build a Python-based pipeline that:

1. Processes synthetic text data (cover letters).
2. Extracts entities and semantic relationships using an LLM.
3. Infers personality traits using the Big Five (OCEAN) model.
4. Consolidates the results into a visualized knowledge graph.
5. Evaluates model performance against gold reference files.

For a more detailed explanation of the methodology, evaluation, and findings, please refer to the full report:  
📄 **[Knowledge Graph Challenge Report.pdf](Knowledge%20Graph%20Challenge%20Report.pdf)**

## Dataset
**Synthetic Cover Letters**
The dataset consists of five synthetic cover letters generated with the assistance of ChatGPT (GPT-5).
Each letter represents a different professional role:

- UX Designer
- Research Scientist
- Data Analyst
- Software Engineer
- Project Manager
  
Each letter includes both structured and expressive elements — such as names, organizations, roles, skills, traits, and motivations — enabling both entity extraction and personality inference.

## Setup
### Requirements
- Python 3.10+
- Ollama installed and running locally
- Llama 3 model pulled:
  ```bash
  ollama pull llama3
  ```
### Install Dependencies
```bash
pip install -r requirements.txt
```

## Execution
1. Open the Jupyter Notebook
  Launch Jupyter and open:
  ```
  Knowledge Graph Challenge.ipynb
  ```
2. Run All Cells Sequentially
  Execute the notebook from top to bottom (Run All) to perform the full pipeline:
  - Data preprocessing and normalization
  - LLM-based record extraction (semantic parsing)
  - Entity extraction
  - Relationship extraction
  - Personality inference
  - Knowledge graph construction
  - Visualization & Export
  - Evaluation
  The notebook automatically reads input files from the data/ directory, stores generated results in the outputs/ directory, and references gold files from the gold/ directory for evaluation.

3. Outputs Generated
  After running, the notebook will produce:
  - entities_per_record.json
  - relations_per_record.json
  - personality_inference.json
  - personality_knowledge_graph.png
  - eval_report.json

4. View the Results
  The Personality Knowledge Graph is displayed directly within the notebook and also saved locally to your device.
  Evaluation results and metrics are printed in the final output cell.

## Results
The system was evaluated against gold-standard files for entity, relation, and personality extraction.  
Results are summarized below (micro-averaged metrics):

### Entity and Relation Extraction Evaluation
| Component | Precision | Recall | F1-score | Notes |
|------------|------------|---------|-----------|--------|
| **Entities (micro)** | 0.556 | 0.556 | 0.556 | TP = 40, FP = 32, FN = 32 |
| **Relations (micro)** | 0.515 | 0.522 | 0.519 | TP = 35, FP = 33, FN = 32 |

### Personality Trait Evaluation
| Trait | Pearson (r) | Spearman (ρ) | MAE |
|-------|--------------|---------------|------|
| **Openness** | 0.18 | 0.22 | 0.08 |
| **Conscientiousness** | 0.96 | 0.73 | 0.03 |
| **Extraversion** | -0.27 | -0.18 | 0.08 |
| **Agreeableness** | 0.27 | 0.18 | 0.06 |
| **Neuroticism** | n/a | n/a | — |

## Report
For a complete discussion of the pipeline design, validation logic, and analysis of results, please refer to:  
**[Knowledge Graph Challenge Report.pdf](Knowledge%20Graph%20Challenge%20Report.pdf)**
