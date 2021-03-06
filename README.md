# Bailarn

The project aims to develop and provide Thai NLP Platform based on deep learning techniques. With this python library, users can train, predict, and evaluate models on their own dataset using the provided deep learning model structure and utilities. Moreover, this project also provides pre-trained models to process Thai text instantly for foundation and application NLP tasks. Each pre-trained model was evaluated and compared across various deep learning techniques proposed in the previous researches in the expensive experiments.

For more information please see the publication "A Comparative Study on Various Deep Learning Techniques for Thai NLP Lexical and Syntactic Tasks on Noisy Data" (JCSSE, 2018).

- **Tokenization**: Identify the boundaries between texts in natural languages to divide these texts into the meaningful unit as word.
- **Word Embedding**: Map a word from the vocabulary to vectors pf real numbers involving a mathematical embedding.
- **Named Entity Recognition**: Predict Named entity of each words in a sentence.
- **Part-of-Speech Tagging**: Predict Part-of-Speech of each words in a sentence.
- **Sentiment Analysis**: Predict the Sentiment of a document including Positive, Neutral and Negative sentiment.
- **Text Categorization**: Predict the pre-defined classes of sentences on the specific domain (Multi-label classification).
- **Keyword Expansion**: Find the related words from the vocabulary to the query word.

## Short introduction for instant models

You could ues all instant models easily by its function. The models will be initialized when `import instant_model` so that means the import process execution time could be long.

```
>>> from bailarn.instant_model import instant_model
>>> text = "ฉันกินข้าว"
>>> instant_model.tokenize(text)
['ฉัน', 'กิน', 'ข้าว']
>>> instant_model.pos_tag(text)
['PPER', 'VV', 'NN']
>>> instant_model.ner(text)
['O', 'O', 'O']
>>> instant_model.sentiment("อาหารมื้อนี้อร่อย") # in Food domain
['POS']
>>> instant_model.categorzation("ใช้ไอโฟนของ AIS อยู่") # in Mobile domain
['iPhone', 'AIS', 'โทรศัพท์มือถือ']
>>> instant_model.keyword_expansion("ไอโฟน") in Mobile domain
[('iphone', 0.7972946763038635),
 ('6', 0.7576655149459839),
 ('แอนดรอย', 0.7489653825759888),
 ('โทรศัพท์', 0.7486546635627747),
 ('ios', 0.7471609115600586),
 ('6s', 0.744852602481842),
 ('รู้สึก', 0.7426965236663818),
 ('5s', 0.7402455806732178),
 ('ตก', 0.7397241592407227),
 ('ชอบ', 0.7394053339958191)]
 >>> instant_model.word_embedding("คำ")
 array([ 4.3708846e-02, -2.4344508e-01, -2.0937651e-01, ..., -8.1250496e-02,  3.1024747e-02,  4.8249800e-02], dtype=float32)
```

Additionally, other examples can be shown in `{task}_introduction.ipynb`

## Performance of instant models

Tokenization, Named Entity Recognition, and Part-of-Speech Tagging tasks were evaluated on BEST2010_I2R test set which was the commercial versoin of BEST corpus from NECTEC. However, the model performaces of Sentiment Analysis and Text Categorization (multi-label) were not reported

- **Tokenization**: f1-score 98.58%
- **Named Entity Recognition**: f1-macro 62.10%, f1-micro 79.59%
- **Part-of-Speech Tagging**: f1-macro 82.41%, f1-micro 95.48%
- **Sentiment Analysis**: N/A
- **Text Categorization**: N/A

## Installation for instant models

Please make sure that you have keras-contrib, or you need to install keras-contrib by its github (also see https://github.com/keras-team/keras-contrib)

```
$ pip install git+https://www.github.com/keras-team/keras-contrib.git
```

Because pre-trained models are huge and can not be stored in Github, we instead uploaded these models to [Google Drive](https://drive.google.com/drive/folders/1duq9zw2jjNR1T39PZ4mOnq8wc-BPW_jC?usp=sharing). So that you are supposed to download the pre-trained model for each task into its `models` folder.

If you encounter any problems with the installation, make sure to install the correct versions of dependencies listed in `requirements.txt` file.

## Authors

- **Amarin Jettakul** - _Initial work_ - [ammarinjtk](https://github.com/ammarinjtk)
- **Chavisa Thamjarat** - _Initial work_ - [jijyisme](https://github.com/jijyisme)
- **Kawin Liaowongphuthorn** - _Initial work_ - [KawinL](https://github.com/KawinL)

See also the list of [contributors](https://github.com/KawinL/Thai_NLP_platform/graphs/contributors) who participated in this project.

## License

This project is licensed under the GNU LESSER GENERAL PUBLIC License

## Acknownledgement

- This project was advised by Assistant Prof. Dr.Peerapon Vateekul, Department of Computer Engineering, Faculty of Engineering, Chulalongkorn University
- The BEST corpus used in this project was supported by Thailand's National Electronics and Computer Technology Center (also see https://www.nectec.or.th/en/)

## References

- [1] Mikolov, Tomas, et al. "Efficient estimation of word representations in vector space." arXiv preprint arXiv:1301.3781(2013).
- [2] Wutthiphat Phuriphatwatthana, Synthai: Thai Word Segmentation and Part-of-Speech Tagging with Deep Learning. ([github](https://github.com/KenjiroAI/SynThai))
- [3] Boonkwan, Prachya, and Thepchai Supnithi. "Bidirectional Deep Learning of Context Representation for Joint Word Segmentation and POS Tagging." In International Conference on Computer Science, Applied Mathematics and Applications, pp. 184-196. Springer, Cham, 2017.
- [4] Liu, Jingzhou, Wei-Cheng Chang, Yuexin Wu, and Yiming Yang. "Deep Learning for Extreme Multi-label Text Classification." In Proceedings of the 40th International ACM SIGIR Conference on Research and Development in Information Retrieval, pp. 115-124. ACM, 2017.
