---
layout: post
draft: true
title: Diabetic retinopathy detection contest: what we did wrong
---

After watching the [awesome video course by Hugo Larochelle](https://www.youtube.com/playlist?list=PL6Xpj9I5qXYEcOhn7TqghAJ6NAPrNmUBH) on neural nets (more on this in the [previous post]({% post_url 2015-07-30-getting-started-with-neural-networks %}) we decided to test our knowledge on some computer vision contest. We looked at [Kaggle](https://www.kaggle.com/competitions) and the only active competition related to computer vision (except for the [digit recognizer contest](https://www.kaggle.com/c/digit-recognizer), for which lots of perfect out-of-the-box solutions exist) was the [Diabetic retinopathy detection contest](https://www.kaggle.com/c/diabetic-retinopathy-detection). This was probably quite hard to become our very first project, but nevertheless we decided to try. The team included [Karen](https://www.linkedin.com/in/mahnerak), [Tigran](https://www.linkedin.com/in/galstyantik), [Hrayr](https://github.com/Harhro94), [Narek](https://www.linkedin.com/pub/narek-hovsepyan/86/b35/380) and [me](https://github.com/Hrant-Khachatrian). Long story short, we finished at the [82nd place](https://www.kaggle.com/c/diabetic-retinopathy-detection/leaderboard), and in this post I will describe in details what we did and what mistakes we made. We hope this will be interesting for those who just start to play with neural networks. Also we hope to get feedback from experts of the field.