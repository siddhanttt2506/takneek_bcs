# QUEST 1 : DO I KNOW YOU?

## Files and Folders

(1) QLoRA_finetune.ipynb is used for fine tuning the model using QLoRA in batches several times (The code in it is for the final batch fine tuning).

(2) dataset_creation.ipynb is used to convert the .jsonl question answer files into a hugging face dataset so that it could be used to fine tune the model.

(3) The dataset folder contains the question with fictional answers of the RAW agents the information of whom we need to change (forget) in .jsonl format.

(4) agents_raw_list.csv contains the name of the raw agents the information of whom we need to change (forget).

(5) new_llm.ipynb is used to ask queries to the new modified LLM.

(6) evaluation_pipeline.ipynb contains a custom made evaluation pipeline for the model.

This is the link for the hugging face model https://huggingface.co/ashishu23/model1/tree/main

Some example datasets used for fine tuning the model are :
1) https://huggingface.co/datasets/ashishu23/dataset1
2) https://huggingface.co/datasets/ashishu23/dataset2
3) https://huggingface.co/datasets/ashishu23/dataset3

## Metrics

(1) HellaSwag -> |0.7345| ± |0.0044|

(2) MMLU -> |0.4499| ± |0.0041|
