# AI-couplet-writer

Welcome! This is our fun project of using AI to write couplets (对对联). Please check out our website!

https://ai-poet.com

## Introduction
- What is couplet (对联)
  - Couplet is a two-liner poem with strict semantic and phoenetic rules
  - See the [Wikipedia](https://en.wikipedia.org/wiki/Antithetical_couplet) (English) page for more details

- What is this project for
  - The model will predict the second line (下联) given the first line (上联)
  - We are a Chinese couple living in California and we love traditional Chinese poems!
  - There are several projects on AI couplet writing (see references below), but this project is unique in the following ways
    - This is the first of its kind written in TensorFlow 2, to the best of our knowledge
    - This model improves from the reference models mostly on (i) emotional (意境) matching; (ii) repeated characters treatment (see the **Model** section below)

## Examples

|     Input     |     Output    |
| ------------- | ------------- |
| 欲把心事付瑶琴  |  且把相思作知己  |
| 半衾幽梦香初散  |  一曲清音韵未央  |
| 应是飞鸿踏泥雪  |  何如落雁寄秋风  |
| 云破月来花弄影  |  雨停风送柳含烟  |
| 别后相思空一水  |  愁中寂寞又几回  |
| 书中自有黄金屋  |  笔下常留白玉簪  |
| 花谢花飞花满天  |  鸟啼鸟语鸟鸣春  |
| 杨柳岸晓风残月  |  芦苇春寒雨乱烟  |


## Model
This is a sequence-to-sequence model with Encoder + Decoder + Attention, schematically shown as below.

![The AI Couplet Model](/doc/schematics.png)

Notable features
- Embedding layer pretrained via Word2Vec
- Beam search decoder
- Format polishing to prevent repeated characters, etc.

## Data & How to Run
- Download the training data (~70k couplets) from [this](https://github.com/wb14123/couplet-dataset) repo
- Set up the model hyperparameters and the file paths in the **baseconfig.ini**
- Install the package dependencies
  - **TensorFlow 2.2.0**
  - Python 3.6.9
  - Numpy 1.18.5
  - Gensim 3.6.0
  - Scikit-Learn 0.22.0
- Train the model
  - Run as ```python train.py```
  - The model parameters will be written to the path set up in the config file
  - Our model on the website was trained on Google Colab Pro for 12 epochs (~1 day)

## Reference
- Seq2seq-couplet by Bin Wang ([Github](https://github.com/wb14123/seq2seq-couplet), [website](https://ai.binwang.me/couplet))
- Seq2seq chinese poetry generation by Simon and Vera ([Github](https://github.com/Disiok/poetry-seq2seq), [Related Paper](https://arxiv.org/abs/1610.09889))
- Microsoft Research/微软亚洲研究院电脑对联系统 ([Website](https://duilian.msra.cn/app/couplet.aspx))
- Open Couplet/中文对联AI ([Github](https://github.com/neoql/open_couplet), [Website](https://couplet.neoql.me/))
- AICHPOEM.COM/诗三百-人工智能诗歌平台 ([Website](https://www.aichpoem.com/#/shisanbai/poem))
- 清华九歌-人工智能诗歌写作系统 ([Website](http://jiuge.thunlp.org/jueju.html))
