---
title: Fastai Lesson 1 Recap
date: 2018-10-23
header:
    overlay_image: https://cdn-images-1.medium.com/max/1600/1*rFY5KxJ7llc0u9cBE6q2LQ.png
    teaser: https://images.unsplash.com/photo-1519452575417-564c1401ecc0?ixlib=rb-0.3.5&ixid=eyJhcHBfaWQiOjEyMDd9&s=c13e16dc570c2c74875bf2303e779e14&auto=format&fit=crop&w=1500&q=80
    og_image: http://course.fast.ai/images/logo.png
    caption: "Image credit: [**Pierre Guillou**](https://medium.com/@pierre_guillou/fastai-how-to-start-663927d4db63)"
    overlay_filter: 0.7
    actions:
        - label: "Learn more"
          url: "https://course.fast.ai/"
excerpt: "An Introduction to Policy Gradient Algorithms"
categories:
    - Deep Learning
    - Academic
tags:
    - Policy Gradient
    - Reinforcement Learning
---
**Notice!** This page is still in progress!
{: .notice--primary}

# Lesson 1 of the Fastai Course 2018

This is a short personal recap of the most important notes from the first fastai lesson.  

## Cloud Services for GPU Computing

Over the last few year there has been a huge spike of cloud computing oppertunities especially for deep learning researchers and by now they are actually really affordable. Just to name a view of them:

- [AWS E2 Instance](), probably the most popular one(offers fastai support)
- [Google Cloud Platform](https://console.cloud.google.com/getting-started?pli=1)
- [Paperspace Gradient](https://www.paperspace.com/gradient) (offers easy fastai integration)
- [Salamander](https://salamander.ai/), $1.17 per hour for a V100 GPU (offers easy fastai integration)
- [Google Colab](https://colab.research.google.com/notebooks/welcome.ipynb#recent=true), as far as I heared there are some issues regarding the fastai support but haven't checked it yet, but it's completly free and comes with a descent K100 GPU.
- [Crestle](https://www.crestle.com/)


## Jupyter Notebooks

Jupyter Notebooks are a pretty neat way to prototype, to explore and to visualize. It comes quit handy because it allows for cell execution which makes it a lot easier than running a whole python file. Furthermore Jupyter Notebook as well as Jupyter Lab are offering some useful utilities, ranging from simple keyboard shortcute to integrated bash like terminals. I will give a short overview on the most important keyboard shortcute and also give a short overview on some interesting Jupyter magic methods.
While in Juypter Notebooks you are either in write mode, typing in code, Markdown/HTML etc., or you are in command mode, for example when you are running cells or hovering over cells.

### Keyboard Shortcuts

`Esc` will put you into command mode while `Enter` will put you into write mode.

#### In Command Mode

|Windows             |Linux              |MacOS                 |Function             |
|--------------------|-------------------|----------------------|---------------------|
|Ctrl + Shift + P    |Ctrl + Shift + P   |Cmd + Shift + P       |Opens Command Prompt |
|h                   |h                  |h                     |Opens Help           |
|a                   |a                  |a                     |Add cell above current cell      |
|b                   |b                  |b                     |Add cell below current cell      |
|f                   |f                  |f                     |Find and replace      |
|o                   |o                  |o                     |Toggle cell output      |
|0+0                 |0+0                |0+0                   |Restart Kernel       |
|d+d                 |d+d                |d+d                   |Delete Cell          |
|Shift + k or Shift + Up                |Shift + k or Shift + Up                 |Shift + k or Shift + Up                  |Select multiple cells in upwards direction      |
|Shift + j or Shift + Down                |Shift + J or Shift + Down                 |Shift + J  or Shift + Down                  |Select multiple cells in downwards direction      |
|Shift + m               |Shift + m                |Shift + m                  |Merge cells    |

### In Write Mode

|Windows             |Linux              |MacOS                 |Function             |
|--------------------|-------------------|----------------------|---------------------|
|Shift + Tab         |Shift + Tab        |Shift + Tab           |Show Docstring       |
|Ctrl + Shift + -    |Ctrl + Shift + -   |Ctrl + Shift + -      |Split cell into two  |
|Ctrl + Enter    |Ctrl + Enter   |Ctrl + Enter      |Run cell  |


### IPython Magics

Magic methods offer some unique functionalities. For example can you track the speed of your functions using the `%time` or `%timit` magic method either right in front of a function or on top of the cell. In case you are using it on top of the cell you have to add an additional `%` to track the speed of the whole cell execution. For example:

```python
%%timit
def power(x, y):
    return x ** y
```

Jupyter will run this cell 10000 times and will return the average computing time. That's a very nice function in case you want to optimize your code. Often times you are unsure what function to use because they are pretty similar: For example during one of my recent projects I had to check whether a Pandas DataFrame is empty or not. Pandas offers the solution `df.empty` but ysome alternatives are `len(df) == 0`, `len(df.index) == 0` or `len(df.columns)`. In the end I was just checking them by using `timeit` and the results were astonishing.

```python
%timit df.empty
%timit len(df) == 0
%timit len(df.index) == 0
%timit len(df.columns) == 0
```

Quit similar observation I made by estimating what row and column indexing to use: `df["col"]` vs `df.col` vs `df.loc[.;col]`. Again huge differences in performance.
So even if they appear to work the same that must not mean they really are. It always worth checking your code for this kind of performance losses and `%time` and `%timeit` will be a huge help.

## The Fastai Library

The fastai library, build on top of [PyTorch](pytorch.org), mainly focuses on four central topics:

1. Computer Vision
2. Natural Language Processing (NLP)
3. Recommendation Systems
4. Tabular Data

## Classifie Images within 4 Lines of Code

Similar to Keras, fastai wraps up a lot of the complexity of the underlying deep learning libraries. But even more than Keras, fastai managed to reduce the code on a bar minimum and still achieves astonishing results. I will demonstarte it below:

```python
data = ImageDataBunch.from_name_re(path_img, fnames, pat, ds_tfms=get_transforms(), size=224)
data.normalize(imagenet_stats)
learn = ConvLearner(data, models.resnet34, metrics=error_rate)
learn.fit_one_cycle(4)
```

First we built a DataBunch object. This will ...


## Evaluate Image Classifier

## Resources
