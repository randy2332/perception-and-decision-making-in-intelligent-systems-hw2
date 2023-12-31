# Tutorial

- run **[data_generator.py](https://github.com/randy2332/NYCU-perception-and-decision-making-in-intelligent-systems-hw2/blob/main/src/data_generator.py)** to get pictures.
    
    ```
    python data_generator.py --dataset <input_datafile> --output <output_file>
    ```
    
- run **[train.py](https://github.com/randy2332/NYCU-perception-and-decision-making-in-intelligent-systems-hw2/blob/main/src/train.py)**  to get the model
    
    ```
    python train.py -cfg <the file you put your .yaml>
    ```
    
    You can see my config shown below. You can adjust the parameters. 
    
    ```
    DATASET:
      root_dataset: ""
      list_train: ./data/dataset_1_training.odgt
      list_val: ./data/dataset_1_validation.odgt
      imgMaxSize: 525
      imgSizes: (300, 375, 450, 525, 600)
      num_class: 101
      padding_constant: 32
      random_flip: True
      segm_downsampling_rate: 4
    DIR: ckpt2/model_dataset1
    MODEL:
      arch_decoder: c1
      arch_encoder: hrnetv2
      fc_dim: 720
    
    TEST:
      batch_size: 1
      checkpoint: epoch_20.pth
      result: ./
    TRAIN:
      batch_size_per_gpu: 4
      num_epoch: 20
      start_epoch: 0
      epoch_iters: 400
      optim: SGD
      lr_decoder: 0.02
      lr_encoder: 0.02
      lr_pow: 0.9
      beta1: 0.9
      weight_decay: 0.0001
      deep_sup_scale: 0.4
      disp_iter: 20
      fix_bn: false
      seed: 304
      workers: 16
    VAL:
      batch_size: 1
      checkpoint: epoch_20.pth
      visualize: True
    ```
    
    I put the ckpt in the  **[link](https://drive.google.com/drive/folders/1LOlHpI4yn2hna21tYqCaTEJ4wOKhp440?usp=drive_link).  Check the model!**
    
- run **[eval_multipro.py](https://github.com/randy2332/NYCU-perception-and-decision-making-in-intelligent-systems-hw2/blob/main/src/eval_multipro.py)**
    
    ```
    python eval_multipro.py -cfg <the file you put .yaml>
    ```
    
    You can see my config shown below. You can adjust the parameters. 
    
    ```
    DATASET:
      imgMaxSize: 525
      imgSizes: (300, 375, 450, 525, 600)
      list_val: "./data/first_validation.odgt"
      num_class: 101
      padding_constant: 32
      random_flip: True
      root_dataset: ""
      segm_downsampling_rate: 4
    DIR: ckpt2/model_dataset2
    MODEL:
      arch_decoder: "c1"
      arch_encoder: "hrnetv2"
      fc_dim: 720
      weights_decoder: None
      weights_encoder: None
    TEST:
      batch_size: 1
      checkpoint: "epoch_7.pth"
      result: ./
    TRAIN:
      batch_size_per_gpu: 4
      beta1: 0.9
      deep_sup_scale: 0.4
      disp_iter: 20
      epoch_iters: 13000
      fix_bn: False
      lr_decoder: 0.02
      lr_encoder: 0.02
      lr_pow: 0.9
      num_epoch: 30
      optim: SGD
      seed: 304
      start_epoch: 0
      weight_decay: 0.0001
      workers: 16
    VAL:
      batch_size: 1
      checkpoint: "epoch_7.pth"
      visualize: True
    ```
    
- run **[load.py](https://github.com/randy2332/NYCU-perception-and-decision-making-in-intelligent-systems-hw2/blob/main/src/load.py)**  to get  the data of floor1 and floor2
