### Baselines
The notebook to train the baseline is provided in the related directory clef2025-checkthat-lab/task3/baselines/English.
The inference script is also provided in relevant directory:

python3 code/nli_inference/veracity_prediction.py --test_path data/raw_data/test_claims_quantemp.json --bm25_evidence_path task3/data/English/bm25_top_100_claimdecomp.json --base_model roberta-large-mnli --model_path <model_path>/<model_name>/model_weights.zip --questions_path data/decomposed_questions/test/test_claimdecomp.csv --output_path finqa_roberta_claimdecomp

where train_data.tsv is the file to be used for training and dev_data.tsv is the file on which doing the prediction.
The baseline is a RoBERTA based NLI model though participants are free to use any model including LLMs. You can also refer to the paper for the idea.


El baseline del ingles depende de 3 archivos>
* English/train_claims_quantemp.json (train_claims) // tiene claim, doc, label //tenemos en español.

* ../../data/English/decomposed_questions_with_mapped_bm25_evidence/train_claimdecomp_evidence_question_mapping.json (train_data) // tiene array
de clain con array de evidences con questions y doc y label // En español tenemos igual pero con formato distinto en m25_evidence/train_spanish_bm25_evidence.json

* ../../data/English/decomposed_questions_with_mapped_bm25_evidence/val_claimdecomp_evidence_question_mapping.json (val data). Igual que anterior


--------PAGINA --------------
Main folder: scorer

Contains a single file, clef2025-checkthat-lab/task3/baselines/English/eval_veracity_prediction.py, that checks the format of a submission and evaluate the various metrics.
The corpus / evidence collection can be found at Evidence collection
Alternatively instead of using whole corpus if you want to use BM25 retrieved evidence for original claims, please refer clef2025-checkthat-lab/task3/data/English/bm25_evidence. The bm25 evidence for training claims and test can be found at train and test bm25

--------SECCION SCORER --------------
To evaluate the output of your model which should be in the output format required, please run the script below:

python3 task3/baselines/English/eval_veracity_prediction.py --test_path clef2025-checkthat-lab/task3/data/English/val_claims_quantemp.json --output_path output/output_example.csv


where output_example.tsv is the output of your model on the dev set / test set and val_claims_quantemp.json is the dev set. You can replye this with test set when released.


--------------
En task 1 se ejecuta: python evaluate.py -g dev_truth.tsv -p dev_predicted.tsv


##
Funciona Spanish evaluation:
python task3/baselines/English/eval_veracity_prediction.py --test_path task3/data/Spanish/val_spanish_claims.json --output_path task3/output/Spanish/val_spanish_claims_verdict_clasificador_claim_doc_zero_shot.csv    


### El 