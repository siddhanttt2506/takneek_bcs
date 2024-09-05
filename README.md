# QUEST 1 : DO I KNOW YOU?

(1) QLoRA_finetune.ipynb is used for fine tuning the model using QLoRA in batches several times (The code in it is for the final batch fine tuning).

(2) dataset_creation.ipynb is used to convert the .jsonl question answer files into a hugging face dataset so that it could be used to fine tune the model.

(3) The dataset folder contains the question with fictional answers of the RAW agents the information of whom we need to change (forget) in .jsonl format.

(4) agents_raw_list.csv contains the name of the raw agents the information of whom we need to change (forget).

This is the link for the hugging face model https://huggingface.co/ashishu23/model1/tree/main

Some example datasets used for fine tuning the model are :
1) https://huggingface.co/datasets/ashishu23/dataset1
2) https://huggingface.co/datasets/ashishu23/dataset2
3) https://huggingface.co/datasets/ashishu23/dataset3
