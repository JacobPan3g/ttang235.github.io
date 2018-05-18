---
layout: post
title: Quick Start on Topic Model
---

Refer to [this article](https://www.analyticsvidhya.com/blog/2016/08/beginners-guide-to-topic-modeling-in-python/)

I did the following to set up the environment:

```
python3 -m venv ~/py_gensim_env
source py_gensim_env/bin/activate
pip install -U gensim
pip install --upgrade pip   # optional
pip install -U nltk
```

I had difficulty downloading nltk data, but [this](https://github.com/gunthercox/ChatterBot/issues/930#issuecomment-322111087)
solved my problem. Also contributed an answer on stack overflow 
[here](https://stackoverflow.com/questions/38916452/nltk-download-ssl-certificate-verify-failed/50406704#50406704)
