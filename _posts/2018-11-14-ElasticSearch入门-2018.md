---
layout:     post
title:      ElasticSearch入门
subtitle:    "\"ElasticSearch\""
date:       2018-11-14
author:     Seven
header-img: img/post-bg-miui6.jpg
catalog: true
tags:
    - ElasticSearch
---

# ElasticSearch入门
## 安装
[elasticsearch 下载地址](https://www.elastic.co/downloads/elasticsearch)

下载完以后，放到一个目录下解压。
目录如下:
![](/img/blog/2018-11-14-1.jpg)

然后在此目录下输入命令:  bin/elasticsearch 
浏览器输入：  http://localhost:9200/ 
返回如下数据则说明启动成功

```
{
  "name" : "ZhRaijM",
  "cluster_name" : "elasticsearch",
  "cluster_uuid" : "kwiltgGgQ8aPVeEdjKbUOQ",
  "version" : {
    "number" : "6.4.3",
    "build_flavor" : "default",
    "build_type" : "tar",
    "build_hash" : "fe40335",
    "build_date" : "2018-10-30T23:17:19.084789Z",
    "build_snapshot" : false,
    "lucene_version" : "7.4.0",
    "minimum_wire_compatibility_version" : "5.6.0",
    "minimum_index_compatibility_version" : "5.0.0"
  },
  "tagline" : "You Know, for Search"
}
```

# 简单介绍
Elasticsearch 是一个实时的分布式搜索分析引擎， 它能让你以一个之前从未有过的速度和规模，去探索你的数据。 它被用作全文检索、结构化搜索、分析以及这三个功能的组合：
* Wikipedia 使用 Elasticsearch 提供带有高亮片段的全文搜索，还有 search-as-you-type 和 did-you-mean 的建议。
* 卫报 使用 Elasticsearch 将网络社交数据结合到访客日志中，实时的给它的编辑们提供公众对于新文章的反馈。
* Stack Overflow 将地理位置查询融入全文检索中去，并且使用 more-like-this 接口去查找相关的问题与答案。
* GitHub 使用 Elasticsearch 对1300亿行代码进行查询。

由此可以看出，Elasticsearch主要还是用于文本类的检索。

Elasticsearch 也是使用 Java 编写的，它的内部使用 Lucene 做索引与搜索，但是它的目的是使全文检索变得简单， 通过隐藏 Lucene 的复杂性，取而代之的提供一套简单一致的 RESTful API。

然而，Elasticsearch 不仅仅是 Lucene，并且也不仅仅只是一个全文搜索引擎。 它可以被下面这样准确的形容：

* 一个分布式的实时文档存储，每个字段 可以被索引与搜索
* 一个分布式实时分析搜索引擎
* 能胜任上百个服务节点的扩展，并支持 PB 级别的结构化或者非结构化数据

Elasticsearch 是面向文档的，意味着它存储整个对象或 文档。Elasticsearch 不仅存储文档，而且 _索引 每个文档的内容使之可以被检索。在 Elasticsearch 中，你 对文档进行索引、检索、排序和过滤--而不是对行列数据。这是一种完全不同的思考数据的方式，也是 Elasticsearch 能支持复杂全文检索的原因。

# 基本概念介绍

## 索引 index
在ES中，index对应到传统的关系型数据库中，可以理解为Database,（一个数据库），在ES中存储数据的这个动作也可以称为索引。
## 类型 type
type 对应到传统的数据库可以理解为 Table。
## 文档 document
document 对应传统的数据库可以理解为Row。document对应的元数据为（index，type， id）这三个元数据确认唯一的document。
index 决定存储的地方；type，代表你存储的是不是同一类型的对象；id，文档的唯一标识。
## field
field 对应数据库中的cloumn

所以用一句话来说：ES集群可以包含多个索引（indices-数据库），每个索引可以包含多个类型（types-表），每个类型包含多个文档（document-行），每个文档里包含多个字段（fields-列）。
