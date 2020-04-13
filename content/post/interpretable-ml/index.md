---
title: Interpretable Machine Learning - How it changed my perception
featured: false
authors:
- admin
Draft: true
Date: 2020-04-13
---

<div style = "text-align: justify">

I had recently been working on a project on classifying cancer from Genomic data. Till now, I usually had been working with deep learning applications either in Image Processing or Computer Vision. It had been a while since I have worked iwth 1D data. In a try to make things less boring, I thought of applying some basic EDA techniques to the data but most of them were in vain since the dataset apparently had 20k+ features. So I was searching for an alternative solution and that's when I came across [Chirtoph Molnar](https://christophm.github.io)'s book: [Interpretable Machine Learning](https://christophm.github.io/interpretable-ml-book/).

<figure>
    <a href = "https://christophm.github.io/interpretable-ml-book/">
    <img src = "https://christophm.github.io/interpretable-ml-book/images/title_page.jpg">
    </a>
</figure>

Before I get started, cross-check if this is what you picture as the monotonous workflow of a *so-called* machine learning project:

* Cleaning, Preprocessing the data
* Some basic data analysis and visualization
* Finding a suitable model to fit the data
* Tweaking until you get a high enough accuracy.

<figure>
    <img src = "course_2.jpg" alt = 'Nevermind'>
    <figcaption> When I didn't use to think about interpretibility</figcaption>
</figure>

If you do hold this boring idea, then trust me, you are missing out.

</div>

## So what is interpretebility? And why is it so important?

<div style = "text-align: justify">

Most of the time us Machine Learning Gurus are obsessed with prediction accuracy and different performance metrics. Indulging in the battle to achieve the highest prediction score, we often a time miss out on the most important aspect of your project - Interpretebility.

Lets time travel a couple of years into the future, where the streets are overtaken by autonomous vehicles. Say a Tesla Robotaxi crashes into a tree, injuring the passenger. Now, if we ask the question - why did the car crash? Would we be able to answer the question?

<figure>
    <a href = "https://www.pexels.com/photo/grayscale-photo-of-wrecked-car-parked-outside-1230677">
    <img src = "car-crash.jpg" alt = 'Imagine a crashed car'>
    <figcaption> Photo by Aleksandr Neplokhov from Pexels </figcaption>
    </a>
</figure>

The problem with most machine learning algorithms is that they are mostly black-boxes. You feed them data and they learn from it. But what they learn is rarely interpretable. The goal of interpretebility is to explain the behavior of these models, which should help us answer the questions about how these models behave, and most importantly, why?

<figure>
    <a href = "https://www.pexels.com/photo/ask-blackboard-chalk-board-chalkboard-356079/">
    <img src = "question-mark.jpg" alt = 'A big question mark'>
    <figcaption> Photo by Pixabay from Pexels </figcaption>
    </a>
</figure>


</div>