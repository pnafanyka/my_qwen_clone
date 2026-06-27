# my_qwen_clone
Here I tried to teach qwen2.5-3B to chat like I do. 

You may find the notebooks hard to replicate given data is not present. I hid is as the model is trained on my personal data.

First qwen fine-tune check-point: https://drive.google.com/drive/folders/1XhSCATin0mojkmgkL6U7G-zmeseAQCYt?usp=sharing
```
lora_config = LoraConfig(
    r=16,
    lora_alpha=32,
    lora_dropout=0.05,
    bias="none",
    task_type="CAUSAL_LM",
    target_modules=["q_proj", "k_proj", "v_proj", "o_proj"]
)

training_args = TrainingArguments(
    output_dir="/content/drive/MyDrive/qwen-russian-lora-2.0",

    per_device_train_batch_size=2,
    gradient_accumulation_steps=8,

    learning_rate=2e-4,
    num_train_epochs=2,

    logging_steps=20,

    save_steps=500,

    eval_strategy="steps",
    eval_steps=500,

    save_total_limit=3,

    report_to="tensorboard",
    logging_dir="/content/drive/MyDrive/qwen-russian-lora-2.0/logs"
)
```

Second qwen fine-tune check-point: https://drive.google.com/drive/folders/1IO3jduvM_1dnZUgYC1mDf95B8gLnTG0-?usp=drive_link
```
lora_config = LoraConfig(
    r=32,
    lora_alpha=64,
    lora_dropout=0.05,
    bias="none",
    task_type="CAUSAL_LM",
    target_modules=["q_proj", "k_proj", "v_proj", "o_proj"]
)

training_args = TrainingArguments(
    output_dir="/content/drive/MyDrive/qwen-russian-lora-2.0",

    per_device_train_batch_size=2,
    gradient_accumulation_steps=2,

    learning_rate=2e-4,
    num_train_epochs=2,

    logging_steps=20,

    save_steps=500,

    eval_strategy="steps",
    eval_steps=500,

    save_total_limit=3,

    report_to="tensorboard",
    logging_dir="/content/drive/MyDrive/qwen-russian-lora-2.0/logs"
)
```
