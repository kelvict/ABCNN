
# ABCNN: Attention-Based Convolutional Neural Network for Modeling Sentence Pairs

#### !!!Caution!!!: Implementation is not complete. I hope having it done very soon!

This is the implementation of **ABCNN**, which is proposed by [Wenpeng Yin et al.](https://arxiv.org/pdf/1512.05193.pdf), on **Tensorflow**.  
It includes all 4 models below:
- BCNN (complete)

    |               |          |   MAP   |   MRR   | Classifier | Epoch |
    |:-------------:|:--------:|:-------:|:-------:|:----------:|:-----:|
    | BCNN(1 layer) |  Results |  0.6660 |  0.6813 |     LR     |   13  |
    |               | Baseline |  0.6629 |  0.6813 |            |       |
    | BCNN(2 layer) |  Results | 0.6762  | 0.6871  |     LR     |   4   |
    |               | Baseline |  0.6593 |  0.6738 |            |       |

- ABCNN-1 (on going)
- ABCNN-2 (on going)
- ABCNN-3 (on going)

### Note:
- Implementation is now only focusing on AS task with [WikiQA](https://www.microsoft.com/en-us/research/publication/wikiqa-a-challenge-dataset-for-open-domain-question-answering/) corpus.
(I originally tried to deal with PI task with [MSRP(Microsoft Research Paraphrase)](https://www.microsoft.com/en-us/download/details.aspx?id=52398) corpus
but it seems that model doesn't work without external features classifier requires.)
- Now working on ABCNNs to make the trained model similar to one in the article.

## Specification
- **preprocess.py**: preprocess (training, test) data and import word2vec to use.
- **train.py**: train a model with configs.
- **test.py**: test the trained model.
- **ABCNN.py**: Implementation of ABCNN models.
- show.py: pyplot codes for test results.
- utils.py: common util functions.
- MSRP_Corpus: MSRP corpus for PI.
- WikiQA_Corpus: WikiQA corpus for AS.
- models: saved models available on Tensorflow.
- experiments: test results on AS tasks.

## Development Environment
- OS: Windows 10 (64 bit)
- Language: Python 3.5.3
- CPU: Intel Xeon CPU E3-1231 v3 3.4 GHz
- RAM: 16GB
- GPU support: GTX 970
- Libraries:
    - **tensorflow** 1.0.1
    - numpy 1.12.1
    - gensim 1.0.1
    - NLTK 3.2.2
    - scikit-learn 0.18.1
    - matplotlib 2.0.0

## Requirements

This model is based on pre-trained Word2vec([GoogleNews-vectors-negative300.bin](https://drive.google.com/uc?id=0B7XkCwpI5KDYNlNUTTlSS21pQmM&export=download)) by T.Mikolov et al.  
You should download this file and place it in the root folder.


## Execution
> (training): python train.py --lr=0.01 --ws=3 --l2_reg=0.0003 --epoch=20 --batch_size=64 --model_type=BCNN --num_layers=2 --data_type=WikiQA

    Paramters
    --lr: learning rate
    --ws: window_size
    --l2_reg: l2_reg modifier
    --epoch: epoch
    --batch_size: batch size
    --model_type: model type
    --num_layers: number of convolution layers
    --data_type: MSRP or WikiQA data

> (test): python test.py --ws=3 --l2_reg=0.0003 --epoch=20 --max_len=40 --model_type=BCNN --num_layers=2 --data_type=WikiQA

    Paramters
    --ws: window_size
    --l2_reg: l2_reg modifier
    --epoch: epoch
    --max_len: max sentence length
    --model_type: model type
    --num_layers: number of convolution layers
    --data_type: MSRP or WikiQA data
    --classifier: Final layout classifier(model, LR, SVM)


## MISC.
- [Original code by the author?](https://github.com/yinwenpeng/Answer_Selection/tree/master/src)
