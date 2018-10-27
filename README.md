# WikipediaCorpus
A wikipedia full text is made into a corpus that can be used in python.But this for **Japanese**.

wiki_wakati_model.model modeled the leaving space between words. 

# Dependency
## Installing "Mecab"
~~~
$ sudo apt-get update
$ sudo apt-get install libmecab1 libmecab-dev mecab mecab-ipadic mecab-ipadic-utf8 mecab-utils
$ pip install mecab-python3
~~~

## Installing "mecab-ipadic-neologd"
~~~
$ git clone --depth 1 https://github.com/neologd/mecab-ipadic-neologd.git
$ cd mecab-ipadic-neologd
$ ./bin/install-mecab-ipadic-neologd -n -a
~~~
Let's see where the neologd was downloaded with the command below.
~~~
$ echo `mecab-config --dicdir`"/mecab-ipadic-neologd"
~~~
If it is displayed as ```/usr/lib/mecab/dic/mecab-ipadic-neologd```, 
Edit the ```/etc/mecabrc``` file and change it to 
```dicdir = /usr/lib/mecab/dic/mecab-ipadic-neologd.```

If it is displayed as ```/usr/lib/x86_64-linux-gnu/mecab/dic/mecab-ipadic-neologd```, Please change to ```dicdir = /usr/lib/x86_64-linux-gnu/mecab/dic/mecab-ipadic-neologd```.
# Setup
Please put one of the files in model.zip in the place you like. However, depending on the OS to be used and the location to be placed, it is necessary to describe it by specifying the file path and absolute path.But, we recommend that you put the wiki_wakati_model.model file or the wiki_wakati_model_neologd.model file where the .py file can access it.

# Usage
Load the model file with the following source code.
~~~python
model = word2vec.Word2Vec.load("./wiki_wakati_model.model")
~~~
It can be used as sentence analysis, word2vec, artificial intelligence data.The following is a sample listing synonyms of "業務".
~~~python
from gensim.models import word2vec
model = word2vec.Word2Vec.load("./wiki_wakati_model.model")
results = model.wv.most_similar(positive=['業務'])
for result in results:
    print(result)
tagger = Mecab.Tagger("")
tagger.parse("")
~~~

# Licence
This software is released under the ***BSD 3-Clause License***, see LICENSE.