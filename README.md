[![Build Status](https://travis-ci.org/cltk/lapos.svg?branch=master)](https://travis-ci.org/cltk/lapos)

# About

The lookkahead PoS Tagger utilizes history based models over globally optimized models


# Build

There are two branches, `master` being for Linux and `apple` being for Mac OS (some changes were made for Clang, see below).

# Use

For full instructions, see `README`. The CLTK's Latin model (based on Perseus treebanks) was made with the following command:

``` shell
$ ./lapos-learn -m ./model latin_training_set.pos
```

Note: You can get this trainined set with `curl -O https://raw.githubusercontent.com/cltk/latin_treebank_perseus/master/latin_training_set.pos`.

For running, use `echo` to pass one sentence at a time:

``` shell
$ echo "He opened the window." | ./lapos -t -m ./model_wsj02-21
He/PRP opened/VBD the/DT window/NN ./.
```


# Changes

To compile on Clang, a few changes need to be made, namely removing `tr1` from, e.g., (`<tr1/unordered_map>` and `td::tr1::unordered_map`).

We also increased the maximum number of tags, from 50 to 2000 (in `crf.h`, commenting out `enum { MAX_LABEL_TYPES = 50 };` and uncommenting `const static int MAX_LABEL_TYPES = 2000;`). Also removed the unnecessary empty-input-line warning in `crf.ppp` (``"warning: empty sentence"``).

# License
Lapos created by Yoshimasa Tsuruoka, Yusuke Miyao, and Jun'ichi Kazama. For all technical details, see `README` and for license `LICENSE`.
