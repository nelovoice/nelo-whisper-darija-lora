# nelo-whisper-darija-lora
This project explores the fine-tuning of the openai/whisper-small model on Moroccan Darija datasets, using both Latin-script and Arabic-script transcriptions. It leverages LoRA (Low-Rank Adaptation) with the PEFT library to reduce the number of trainable parameters and accelerate training.


📚 Dataset
We use two Hugging Face datasets:

atlasia/DODa-audio-dataset for training
Snousnou/Moroccan-Darija-ASR for testing

Before training, both datasets are cleaned to filter out:

Empty transcriptions

Silent or invalid audio samples

🧪 Objective
Improve Whisper’s ability to transcribe Darija dialect using a lightweight fine-tuning method (LoRA) that:

Trains only a subset of parameters

Is faster and memory-efficient

Keeps the base model intact

Training process

We fine-tuned the whisper-small model using LoRA for 500 update steps, with a small batch size of 2 and gradient accumulation over 4 steps—making it as if we were training on 8 examples at a time. The learning rate was set to 1e-4, and we used mixed precision (FP16) to speed up training and reduce memory usage. We saved and evaluated the model every 100 steps to monitor progress.

The resulting model is saved in the `whisper-darja-lora/` folder.