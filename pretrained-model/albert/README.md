# ALBERT-Bahasa

Thanks to official implementation from Google, https://github.com/google-research/google-research, Malaya just create custom pretraining and optimizer to support multigpus.

## Table of contents
  * [Objective](#objective)
  * [Acknowledgement](#acknowledgement)
  * [How-to](#how-to)
  * [Citation](#citation)
  * [Donation](#donation)

## Objective

1. There is no multilanguage implementation of ALBERT, and obviously no Bahasa Malaysia implemented. So we decided to train ALBERT from scratch and finetune using available dataset we have. [Dataset we use for pretraining](https://github.com/huseinzol05/Malaya-Dataset#dumping).

2. Provide **BASE** and **TINY** ALBERT for Bahasa.

## Acknowledgement

Thanks to [Im Big](https://www.facebook.com/imbigofficial/), [LigBlou](https://www.facebook.com/ligblou), [Mesolitica](https://mesolitica.com/) and [KeyReply](https://www.keyreply.com/) for sponsoring AWS, Google and GPU clouds to train ALBERT for Bahasa.

## How-to

1. Create pretraining dataset,

```bash
python3 create-pretraining.py
```

2. Execute pretraining,

**ALBERT required TPU to pretrain. I never had successful pretraining on GPUs even on a small dataset.**

```bash
python3 run_pretraining.py \
--input_file=gs://bucket/albert-dataset/*.tfrecord \
--output_dir=gs://bucket/albert-base-actual \
--do_train=True --do_eval=False \
--albert_config_file=gs://bucket/setting/BASE_config.json \
--train_batch_size=1040 --max_seq_length=512 --max_predictions_per_seq=20 \
--num_train_steps=150000 --num_warmup_steps=3125 --learning_rate=1e-4 \
--save_checkpoints_steps=10000 --use_tpu=True --tpu_name=node-1 --tpu_zone=us-central1-a
```

## Citation

1. Please citate the repository if use these checkpoints.

```
@misc{Malaya, Natural-Language-Toolkit library for bahasa Malaysia, powered by Deep Learning Tensorflow,
  author = {Husein, Zolkepli},
  title = {Malaya},
  year = {2018},
  publisher = {GitHub},
  journal = {GitHub repository},
  howpublished = {\url{https://github.com/huseinzol05/malaya}}
}
```

2. Please at least email us first before distributing these checkpoints. Remember all these hard workings we want to give it for free.
3. What do you see just the checkpoints, but nobody can see how much we spent our cost to make it public.

## Donation

<a href="https://www.patreon.com/bePatron?u=7291337"><img src="https://static1.squarespace.com/static/54a1b506e4b097c5f153486a/t/58a722ec893fc0a0b7745b45/1487348853811/patreon+art.jpeg" width="40%"></a>

Or, One time donation without credit card hustle, **7053174643, CIMB Bank, Husein Zolkepli**
