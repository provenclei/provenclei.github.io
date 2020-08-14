---
layout: post
title: 'Spark DataFrame and Spark SQL'
date: 2020-4-1
author: 被水淹死的鱼
color: blue
cover: 'https://ss2.bdstatic.com/70cFvnSh_Q1YnxGkpoWK1HF6hhy/it/u=370960796,3925594138&fm=26&gp=0.jpg'
tags: 大数据 Spark
---

# Spark DataFrame and Spark SQL

目录：
* 目录
{:toc}

![](../assets/hdfs/spark.png)

## 总览
Spark SQL 是 Spark 处理结构化数据的一个模块, 与基础的 Spark RDD API 不同, Spark SQL 提供了查询结构化数据及计算结果等信息的接口.在内部, Spark SQL 使用这个额外的信息去执行额外的优化.有几种方式可以跟 Spark SQL 进行交互, 包括 SQL 和 Dataset API.当使用相同执行引擎进行计算时, 无论使用哪种 API / 语言都可以快速的计算。

## SQL
Spark SQL 的功能之一是执行 SQL 查询，Spark SQL 也能够被用于从已存在的 Hive 环境中读取数据。当以另外的编程语言运行SQL 时, 查询结果将以 Dataset/DataFrame的形式返回，也可以使用 命令行或者通过 JDBC/ODBC与 SQL 接口交互.

## DataFrames
从RDD里可以生成类似大家在pandas中的DataFrame，同时可以方便地在上面完成各种操作。

### 构建SparkSession

Spark SQL中所有功能的入口点是 SparkSession 类. 要创建一个 SparkSession, 仅使用 SparkSession.builder()就可以了:

```python
from pyspark.sql import SparkSession

spark = SparkSession \
    .builder \
    .appName("Python Spark SQL") \
    .config("spark.some.config.option", "some-value") \
    .getOrCreate()
```
