## What is the project?
pyace: A python implementation of automatic chord estimation (ACE) from audio

## Why this project?
This is a super light version that derives from my [PhD thesis](https://github.com/tangkk/phd-thesis-junqi-deng/blob/master/junqi-thesis-hku.pdf). The original [code](https://github.com/tangkk/tangkk-mirex-ace) of this work is written in matlab. So I try to port some of those code into python. But this is by no means a direct porting. It is meant to be minimalist version of ACE, which keeps only the algorithmic gist of the original work.

Compared with the [original version](https://github.com/tangkk/tangkk-mirex-ace) which supports sevenths chords and inversions, this piece of code currently only supports maj and min triads, and it has much lighter (only a few lines of) feature extraction and segmentation codes, which leverages librosa and hmmlearn.

## What are the dependencies?
It depends on [librosa](https://github.com/librosa/librosa) for feature extraction and [hmmlearn](http://hmmlearn.readthedocs.io/en/stable/) for chord segmentation (as well as labeling if in the simple model)

Also install [keras](https://keras.io/) (and [theano](http://www.deeplearning.net/software/theano/) or [tensorflow](http://tensorflow.org/) also) to use fcnn or rnn based ace, otherwise you could only run it in "simple" model.


## How to install it?
```
pip install pyace
```
This should automatically install all dependencies. 

## How to use it?
First of all you should import the module by calling:
```
import pyace
```

It basically provide two simple interfaces:

```
pyace.simpleace(songpath, respath)
```
or
```
pyace.deepace(songpath, respath, modelpath, acemode)
```
## How to use it without installation?
You could just take the source code and run it as:
```
python pyace.py [songpath] [acemode] [modelpath]
```
For example:
The acemode can be either 'simple', 'fcnn' or 'rnn'.'

for example try the following lines:
```
python pyace.py aizheni.mp3 simple
python pyace.py aizheni.mp3 rnn ./model/lstmrnn512/CJKURB.cg.model
```
The pretrained models as well as the testcases can be downloaded [here](http://tangkk.net/me/pyace/models.zip)

## Can I modify the code?
This is a very minimal version of ACE. You are strongly encouraged to take this piece of code away and do whatever you want to.

## How can I evaluate the results?
Please refer to the evaluation script provided (pyace/aceeval.py and eval.sh) for the evaluation process.
These evaluation scripts rely on the [MusOOEvaluator](https://github.com/jpauwels/MusOOEvaluator)

## License
This software is under BSD License. For commercial use of this software, please contact the author.



