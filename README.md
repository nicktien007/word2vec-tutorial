# 使用 gensim 訓練中文詞向量

## [教學文件](http://zake7749.github.io/2016/08/28/word2vec-with-gensim/)

## 套件需求

* jieba
```
pip3 install jieba
```
* gensim
```
pip3 install -U gensim
```

## 訓練流程

1.取得[中文維基數據](https://dumps.wikimedia.org/zhwiki/20160820/zhwiki-20160820-pages-articles.xml.bz2)，本次實驗是採用 2016/8/20 的資料，若需更新的資料可以前往[維基百科:資料庫下載](https://zh.wikipedia.org/wiki/Wikipedia:%E6%95%B0%E6%8D%AE%E5%BA%93%E4%B8%8B%E8%BD%BD)下載

2.使用`wiki_to_txt.py`從xml格式裡提取出維基文章

```
python3 wiki_to_txt.py zhwiki-20160820-pages-articles-multistream.xml.bz2
```
3.使用 opencc 統一將維基文章轉換為繁體中文
```
opencc -i wiki_texts.txt -o wiki_zh_tw.txt -c s2tw.json
```
4.使用`jieba`對文本斷詞，並去除停用詞
```
python3 segment.py
```
5.使用`gensim`的word2vec模型進行訓練
```
python3 train.py
```
6.測試我們訓練出的模型
```
python3 demo.py
```
