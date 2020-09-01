# High Granularity Multilingual Named Entity Recognition

BERT-based high granularity multilingual named entity recognition

Use this repository to train a BERT-based NER model on 96 labels based on the paper UNER: Universal Named-Entity Recognition
Framework (http://ceur-ws.org/Vol-2611/short1.pdf) on a dataset collected from wikipedia.


# Requirements
git clone https://github.com/huggingface/transformers
cd transformers
pip install .
git pull
pip install --upgrade

# Data
Download the labels.txt file and the train, test, and dev datasets from the repo. To run the code using script below, place files into appropriate folder structure.

# Run
python run_ner.py --data_dir data --labels labels.txt --model_name_or_path bert-base-multilingual-cased --output_dir output --max_seq_length  512 --num_train_epochs 6 --per_device_train_batch_size 16 --per_device_eval_batch_size 16 --save_steps 750 --seed 1 --do_train --do_eval --do_predict --overwrite_output_dir
