# Thanks

* Thanks to nanoGPT help me to create an AI story teller. You can find more from [nanoGTP](https://github.com/karpathy/nanoGPT).

# nanoGPT-H.Potter

* H.Potter-GPT is an AI story teller, you can give the key words for anything you want to enjoy magic story.
* H.Potter-GPT is only trainning based on 'Harry Potter' by J.K.Rowlling.
* You can obtain the dataset from [my kaggle home](https://www.kaggle.com/datasets/jalenzhong/harry-potter-txt-file).

## install

```
pip install torch numpy transformers datasets tiktoken wandb tqdm
```

Dependencies:

- [pytorch](https://pytorch.org) <3
- [numpy](https://numpy.org/install/) <3
- `transformers` for huggingface transformers <3 (to load GPT-2 checkpoints)
- `datasets` for huggingface datasets <3 (if you want to download + preprocess OpenWebText)
- `tiktoken` for OpenAI's fast BPE code <3
- `wandb` for optional logging <3
- `tqdm` for progress bars <3

## quick start

Notice:

> I tested all the files on windows system with GPU, so you need to change the command blow for fitting your own system. More information to check nanoGPT.

* prepare the dataset:

```
python data/harrypotter/prepare.py
```

This creates a `train.bin` and `val.bin` in that data directory. Now it is time to train your GPT. The size of it very much depends on the computational resources of your system:

* train  H.Potter-GPT:

```
python train.py config/train_harrypotter.py --device=cuda --compile=False
```

2000 years later...................

* select the best model by pointing the sampling script at this directory and give the **"keyword"**:

```
python sample.py --out_dir=out-harrypotter --start="Harry hoped"
```

if you do not have a GPU, you can try:

```
python sample.py --out_dir=out-harrypotter --device=cpu --start="Harry hoped"
```

* result of keywords "Harry hoped":

```
---------------
Harrt hoped that he could have found out what happened in the mirror so far he was looking forward to see how it was .
An enormous , black dog Harry was standing on the bed .
Hermione was wearing a long , bulging shabby old handkerchief .
" Come on , have you , " said Harry , scanning the book and seizing a large banner she had hit the Invisibility Cloak , and Ron's hand was now raised .
" Great , " said Hagrid , pointing at the picture in front of him , " I'd like to wait to see more owls in the first task , but this is a problem , I'm sorry , but " " Hagrid ! "
said Hermione loudly , pulling a large bag from the table at the pair of them .
" This way ter get one o ' term , Hagrid ! "
" Hagrid ! "
said Ron , gesturing toward them .
---------------
```

As you can see, harry-GPT is not very "smart", I  but it is still a magic!

## Analysis

GPT performs better in modeling the "Shakespeare" dataset( You can find the result from [&#34;Shakspeare&#34;](https://github.com/karpathy/nanoGPT) ) compared to "Harry Potter".

The reason for this analysis is that "Harry Potter" is a dataset of novels where the word sequences are more random compared to a dataset of poems. However, for the Nona GPT model, its capacity is not sufficient to effectively model the complexity of a novel dataset like "Harry Potter".

These are the results I obtained from training on the "Harry Potter" dataset with a learning rate of 10e-6, 8 GPT blocks, and 40,000 iterations. On the other hand, for the "Shakespeare" dataset, I used a learning rate of 10e-3, 6 GPT blocks, and trained for 5,000 iterations.

## Other Example:

* “Hermione took”:

  ```
  ---------------
  Hermione took a deep breath and looked around at Harry , who was so interested in the crowd that they were sitting in the Great Hall , wondering whether he had the only three of them .
  Snape had heard her mutter and watched Harry feel very good chance .
  The Gryffindors were waiting in the Hall at once , but there was a heavy pause .
  " That's the first time , " said Hermione in a voice as they passed the Gryffindor common room .
  " It's all right , " said Ron blankly , " we'll be in the corridor without Fred and George . "
  " You can't be able to stay , " said Harry .
  It was the Marauder's Map now .
  " Hermione , " Hermione spat , at once .
  " I've got to get one of the dormitory . "
  " You've never been thinking of the Dungbombs , " said Ron .
  ---------------
  ```
* "Roan ate":

  ```
  ---------------
  Roan ate their position , and Harry noticed that the others exchanged looks with a slight expression and snatching up for his left hand .
  " What's that supposed to have ? "
  said Ron quickly .
  " Well , " said Hermione , who was now looking at Ron and Ginny , who was sitting beside him .
  " Where's there ? "
  " Yeah , I've been getting better with more things than that , " said Ron , beaming .
  " It's not safe . "
  Harry , Ron , and Hermione went down to the castle and went to bed with all their bags and back to the Great Hall , their first morning .
  It was nearly time , but Hermione had already packed her homework all day .
  " You'd like to get back to Charms , " said Harry faintly .
  " Well , I thought you'd better tell , " said Hermione , rubbing her hair so that Harry and Ron looked up at each other as though she was not daring to laugh .
  ---------------
  ```
* "Voldemort was reborn":

  ```
  ---------------
  Voldemort was reborn from Azkaban .
  But he just knows how he'd have come back to the Ministry for his time .
  His parents were hiding , just for instance , even if he'd be able to kill Voldemort . "
  " And he was delighted , " said the boy , " so he must have been able to talk to him on his school , he was on his mother's right day .
  Was that Voldemort's sake on the place ? "
  " I didn't think he hadn't , " said Harry .
  " Because he wants to take the time , " said Dumbledore .
  " I'm sure he's not a good idea who's looking for him , but he is getting too much more friends than that . "
  " But , " said Harry , his voice rising slightly .
  " Where are you ? "
  " He's in , " said Dumbledore , his voice echoing up the spiral staircase , " Sirius is going to have enough of the Order , you know .
  ---------------
  ```
