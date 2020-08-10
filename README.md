# High Granularity Multilingual Named Entity Recognition

BERT-based high granularity multilingual named entity recognition
Requirements
python3
pip3 install -r requirements.txt
Run
python run_ner.py --data_dir=data/ --bert_model=bert-base-cased --task_name=ner --output_dir=out_base --max_seq_length=128 --do_train --num_train_epochs 5 --do_eval --warmup_proportion=0.1

Result
BERT-BASE
Validation Data
             precision    recall  f1-score   support

        PER     0.9677    0.9745    0.9711      1842
        LOC     0.9654    0.9711    0.9682      1837
       MISC     0.8851    0.9111    0.8979       922
        ORG     0.9299    0.9292    0.9295      1341

avg / total     0.9456    0.9534    0.9495      5942
Test Data
             precision    recall  f1-score   support

        PER     0.9635    0.9629    0.9632      1617
        ORG     0.8883    0.9097    0.8989      1661
        LOC     0.9272    0.9317    0.9294      1668
       MISC     0.7689    0.8248    0.7959       702

avg / total     0.9065    0.9209    0.9135      5648
Pretrained model download from here
BERT-LARGE
Validation Data
             precision    recall  f1-score   support

        ORG     0.9288    0.9441    0.9364      1341
        LOC     0.9754    0.9728    0.9741      1837
       MISC     0.8976    0.9219    0.9096       922
        PER     0.9762    0.9799    0.9781      1842

avg / total     0.9531    0.9606    0.9568      5942
Test Data
             precision    recall  f1-score   support

        LOC     0.9366    0.9293    0.9329      1668
        ORG     0.8881    0.9175    0.9026      1661
        PER     0.9695    0.9623    0.9659      1617
       MISC     0.7787    0.8319    0.8044       702

avg / total     0.9121    0.9232    0.9174      5648
Pretrained model download from here
Inference
from bert import Ner

model = Ner("out_base/")

output = model.predict("Steve went to Paris")

print(output)
'''
    [
        {
            "confidence": 0.9981840252876282,
            "tag": "B-PER",
            "word": "Steve"
        },
        {
            "confidence": 0.9998939037322998,
            "tag": "O",
            "word": "went"
        },
        {
            "confidence": 0.999891996383667,
            "tag": "O",
            "word": "to"
        },
        {
            "confidence": 0.9991968274116516,
            "tag": "B-LOC",
            "word": "Paris"
        }
    ]
'''
