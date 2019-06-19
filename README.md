# CopyCat

# Main changes are in:

https://github.com/ImperialNLP/CopyCat/blob/master/tensor2tensor/tensor2tensor/models/transformer.py
https://github.com/ImperialNLP/CopyCat/blob/master/tensor2tensor/tensor2tensor/layers/common_layers.py
https://github.com/ImperialNLP/CopyCat/blob/master/tensor2tensor/tensor2tensor/layers/modalities.py

**My comments in all those files start with #JI:**

data bins generation config:

https://github.com/ImperialNLP/CopyCat/blob/master/tensor2tensor/data_config.py

**Example command:**

for training:

CUDA_VISIBLE_DEVICES=0 tensor2tensor/bin/t2t-trainer --t2t_usr_dir=zhen_wmt17 --data_dir=/home/you/data --output_dir=/home/you/system --problem=delib_zhen_wmt17 --model=transformer --hparams_set=zhen_wmt17_transformer_big_v1 --eval_steps=100 --hparams='batch_size=30,use_fixed_batch_size=True,max_length=451,learning_rate=0.05' --train_steps=300000 --keep_checkpoint_max=100000 --save_checkpoints_secs=3600 >> log.txt 2>&1 &

for testing (works only for binaries):

CUDA_VISIBLE_DEVICES=0 tensor2tensor/bin/t2t-decoder --t2t_usr_dir=zhen_wmt17 --data_dir=/home/you/data-test --output_dir=/home/you/system --problem=delib_zhen_wmt17 --model=transformer --hparams_set=zhen_wmt17_transformer_big_v1 --decode_hparams="beam_size=1,batch_size=30" --decode_to_file=out_file


