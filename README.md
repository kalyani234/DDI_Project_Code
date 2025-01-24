# Drug-Drug Interaction (DDI) Prediction Pipeline

## Aim
To develop an efficient machine learning pipeline for predicting Drug-Drug Interactions (DDIs) using Artificial Intelligence (AI) techniques and advanced protein/drug embeddings.

## Objectives
1. Collect, preprocess, and integrate multi-modal datasets (drug-target mappings, interaction labels, protein sequences).
2. Extract meaningful features from protein sequences and drug structures using AI models such as ProtBERT.
3. Implement machine learning models to predict the likelihood of DDIs.
4. Evaluate model performance using robust metrics like F1 Score, Precision, and Recall.
5. Deploy the best-performing model for real-world DDI prediction.

---

## Why Use AI in DDI Prediction?
Drug-drug interactions can lead to severe adverse effects, making early detection critical. Traditional methods for DDI prediction, such as experimental or rule-based approaches, are time-consuming and limited in scalability.

AI is a game-changer for DDI prediction because:
- **Pattern Recognition**: AI models can learn intricate relationships between drugs and their target proteins.
- **Efficiency**: Reduces time and cost associated with manual testing.
- **Scalability**: AI models can analyze large datasets of drug interactions.
- **Advanced Representation**: AI models like ProtBERT encode biochemical and structural information from protein sequences, capturing properties that traditional methods miss.

---

## Pipeline Description

### Input Files
1. **drug_targets.csv**: Maps drugs to their target proteins.
   - **Columns**: `drug_id`, `drug_name`, `protein_id`, `protein_name`, `protein_title`

2. **ddi_labels.csv**: Contains drug pairs and their interaction labels (binary).
   - **Columns**: `drug1`, `drug1_name`, `drug2`, `drug2_name`, `label`, `description`

3. **protein_sequences.fasta**: FASTA file with sequences of target proteins.
   - **Format**: `>protein_id` followed by the amino acid sequence.

---

### Steps in the Pipeline
1. **Data Preprocessing**
   - Remove duplicate records and handle missing data.
   - Balance class distribution using SMOTE for DDI labels.

2. **Feature Engineering**
   - **Protein Embeddings**: Use ProtBERT to encode protein sequences.
   - **Drug Embeddings**: Aggregate protein embeddings for each drug.
   - Optionally, include molecular fingerprints for drugs (if structural data is available).

3. **Drug-Target Pair Feature Creation**
   - Combine embeddings of drug pairs into feature vectors.

4. **Data Splitting**
   - Split the data into training, validation, and test sets (e.g., 70/15/15).

5. **Feature Scaling and Dimensionality Reduction**
   - Standardize features using StandardScaler.
   - Reduce dimensions using Truncated Singular Value Decomposition (SVD).

6. **Model Training**
   - Train models like Random Forest, XGBoost, and Neural Networks.
   - Tune hyperparameters using GridSearchCV.

7. **Model Evaluation**
   - Evaluate performance with metrics like Accuracy, F1 Score, Precision, and Recall.

8. **Results Interpretation**
   - Compare models and select the best-performing one.
   - Perform error analysis to identify areas for improvement.

