# HybridQA
This repository contains the dataset and code for paper "HybridQA: A Dataset of Multi-Hop Question Answeringover Tabular and Textual Data"


# Running Stage1:
Running training command for stage1 using BERT-base-uncased as follows:
```
CUDA_VISIBLE_DEVICES=0 python train_stage12.py --do_lower_case --do_train --train_file preprocessed_data/stage1_training_data.json --predict_file preprocessed_data/stage1_dev_data.json --learning_rate 2e-6 --option stage1 --num_train_epochs 3.0
```
Running training command for stage1 using BERT-base-cased as follows:
```
CUDA_VISIBLE_DEVICES=0 python train_stage12.py --model_name_or_path bert-base-cased --do_train --train_file preprocessed_data/stage1_training_data.json --predict_file preprocessed_data/stage1_dev_data.json --learning_rate 2e-6 --option stage1 --num_train_epochs 3.0
```

Running training command for stage2 as follows:
```
CUDA_VISIBLE_DEVICES=0 python train_stage12.py --do_lower_case --do_train --train_file preprocessed_data/stage2_training_data.json --predict_file preprocessed_data/stage2_dev_data.json --learning_rate 5e-6 --option stage2 --num_train_epochs 3.0
```

Running training command for stage3 as follows:
```
CUDA_VISIBLE_DEVICES=0 python train_stage3.py --do_train  --do_lower_case   --train_file preprocessed_data/stage3_training_data.json   --predict_file preprocessed_data/stage3_dev_data.json   --per_gpu_train_batch_size 12   --learning_rate 3e-5   --num_train_epochs 4.0   --max_seq_length 384   --doc_stride 128  --threads 8
```

Model Selction command for stage1 and stage2 as follows:
```
CUDA_VISIBLE_DEVICES=0 python train_stage12.py --do_lower_case --do_eval --option stage1 --output_dir stage1/2020_04_01_20_03_35/ --predict_file preprocessed_data/stage1_dev_data.json
```

Evaluating command for stage1 and stage2 as follows:
```
CUDA_VISIBLE_DEVICES=0 python train_stage12.py --stage1_model stage1/2020_03_29_14_32_54/checkpoint/ --stage2_model stage2/2020_03_29_14_33_28/checkpoint/ --do_lower_case --predict_file preprocessed_data/dev_inputs.json --do_eval --option stage12
```

Evaluating command for stage3 as follows:
```
CUDA_VISIBLE_DEVICES=0 python train_stage3.py --model_name_or_path stage3/2020_03_27_23_44_59/checkpoint/ --do_stage3   --do_lower_case  --predict_file predictions.intermediate.json --per_gpu_train_batch_size 12  --max_seq_length 384   --doc_stride 128 --threads 8
```