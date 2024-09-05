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

## Evaluating our finetuned model on Hellaswag and MMLU

To evaluate our model on these benchmarks, we used the popular CLI tool named `llm-evaluation-harness`. This tool is designed to streamline the process of evaluating language models on various benchmarks. You can find the repository for this tool [here](https://github.com/EleutherAI/lm-evaluation-harness).

Instructions to install the tool :

### To install the `lm-eval` package from the github repository, run:
```bash
git clone https://github.com/EleutherAI/lm-evaluation-harness
cd lm-evaluation-harness
pip install -e .
```

Below is the command we used for the evaluation:

```bash
lm_eval --model hf \
        --model_args pretrained=qu-bit/SuperLLM,parallelize=True,peft=ashishu23/model1 \
        --load_in_4bit=True \
        --tasks hellaswag,mmlu \
        --device cuda:0 \
        --batch_size auto:4
```

This command specifies the following:

- `--model hf`: Indicates that the model type is from Hugging Face.
- `--model_args pretrained=qu-bit/SuperLLM,parallelize=True,peft=ashishu23/model1`: Specifies the pretrained model and additional arguments such as parallelization and PEFT (Parameter-Efficient Fine-Tuning).
-  `--load_in_4bit=True`: Loads the model using 4bit quantization.
- `--tasks hellaswag,mmlu`: Lists the benchmarks used for evaluation.
- `--device cuda:0`: Specifies the device to be used for evaluation (in this case, GPU).
- `--batch_size auto:4`: Sets the batch size to be automatically.

You can use this command to replicate our evaluation setup. 

The results shown below show that we have achieved the finetuning with minimal intereference to the core functioning of the LLM.

![WhatsApp Image 2024-09-05 at 15 16 52_b1c646a1](https://github.com/user-attachments/assets/42cf093d-103e-4186-b519-f320c6aa8495)

## Final Results

### Response when prompted about RAW Agents :

![results/Screenshot 2024-09-05 205221.png](https://github.com/siddhanttt2506/takneek_bcs/blob/main/results/Screenshot%202024-09-05%20205221.png)

![results/Screenshot 2024-09-05 210244.png](https://github.com/siddhanttt2506/takneek_bcs/blob/main/results/Screenshot%202024-09-05%20210244.png)

![results/Screenshot 2024-09-05 211458.png](https://github.com/siddhanttt2506/takneek_bcs/blob/main/results/Screenshot%202024-09-05%20211458.png)

So we can model responses with fabricated information abouts these agents

### Response when prompted about queries unrelated to RAW Agents :

![results/Screenshot 2024-09-05 211331.png](https://github.com/siddhanttt2506/takneek_bcs/blob/main/results/Screenshot%202024-09-05%20211331.png)

Normal Responses to these queries

