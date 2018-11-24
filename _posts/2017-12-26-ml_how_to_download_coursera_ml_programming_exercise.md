---
layout: post
title: 如何下载Coursera Neural Network编程作业
date: 2017-12-26
tag: Machine Learning
---

>* 1、打开jupyter notebook,点击file open
>* 2、进入笔记本后，点击文件夹小图标进入根目录
>* 3、新建download.ipynb文件
>* 4、在download.ipynb中执行命令:    !tar cvfz notebook.tar.gz *
>* 4.1、解决软链接问题,采用以下命令:     !tar -zcvphf a1.tar.gz *
>* 5、执行完第4步后会在根目录生成一个notebook.tar.gz文件，选中并下载
>* 6、解压见证奇迹

参考自：[Download all files in a path on Jupyter notebook server](https://stackoverflow.com/questions/43042793/download-all-files-in-a-path-on-jupyter-notebook-server/47355754#47355754)
