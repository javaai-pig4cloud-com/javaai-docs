---
title: 向量化及存储
---

## Embedding模型简介

Embedding模型是将文本数据（如词汇、短语或句子）转换为数值向量的工具，这些向量捕捉了文本的语义信息，可用于各种自然语言处理（NLP）任务。

### 工作原理
Embedding模型将文本映射到高维空间中的点，使语义相似的文本在这个空间中距离较近。例如，"猫"和"狗"的向量可能会比"猫"和"汽车"的向量更接近。

### 优点
- 捕捉复杂的词汇关系（如语义相似性、同义词、多义词）
- 超越传统词袋模型的简单计数方式
- 动态嵌入模型（如BERT）可根据上下文生成不同的词向量

![Embedding示意图](https://minio.pigx.top/oss/202410/1728219277.jpg)

## LangChain支持的向量数据库

LangChain支持多种向量数据库，每种数据库具有不同的特性。以下是部分支持的向量数据库及其功能：

| 向量存储 | 存储元数据 | 按元数据过滤 | 移除向量 |
| --- | --- | --- | --- |
| 内存存储 | ✅ | ✅ | ✅ |
| Astra DB | ✅ |  |  |
| Azure AI Search | ✅ | ✅ | ✅ |
| Azure CosmosDB Mongo vCore | ✅ |  |  |
| Azure CosmosDB NoSQL | ✅ |  |  |
| Cassandra | ✅ |  |  |
| Chroma | ✅ | ✅ | ✅ |
| Couchbase | ✅ | ✅ |  |
| Elasticsearch | ✅ | ✅ | ✅ |
| Infinispan | ✅ |  |  |
| Milvus | ✅ | ✅ | ✅ |
| MongoDB Atlas | ✅ | 仅支持原生过滤 |  |
| Neo4j | ✅ |  |  |
| OpenSearch | ✅ |  |  |
| Oracle | ✅ | ✅ | ✅ |
| PGVector | ✅ | ✅ | ✅ |
| Pinecone | ✅ | ✅ | ✅ |
| Qdrant | ✅ | ✅ |  |
| Redis | ✅ |  |  |
| Tablestore | ✅ | ✅ | ✅ |
| Vearch | ✅ |  |  |
| Vespa |  |  |  |
| Weaviate | ✅ | ✅ |  |

## 文本向量化

使用OpenAI的Embedding模型进行文本向量化的示例代码：

```java
@Bean
public EmbeddingModel embeddingModel() {
    return OpenAiEmbeddingModel.builder()
            .apiKey(System.getenv("DASHSCOPE_KEY"))
            .modelName("text-embedding-v3")
            .baseUrl("https://dashscope.aliyuncs.com/compatible-mode/v1")
            .build();
}

Embedding queryEmbedding = embeddingModel.embed("host报错请检查环境").content();
```

## Qdrant向量库存储

Qdrant是一个高性能的向量数据库，用于存储嵌入并进行快速的向量搜索。

### 安装Qdrant

使用Docker安装Qdrant：

```bash
docker run -p 6333:6333 -p 6334:6334 qdrant/qdrant
```

- 端口6333：用于HTTP API
- 端口6334：用于gRPC API

![Qdrant运行截图](https://minio.pigx.top/oss/202410/1728373244.png)

### 集成LangChain4j与Qdrant

1. 添加Maven依赖：

```xml
<dependency>
   <groupId>dev.langchain4j</groupId>
   <artifactId>langchain4j-qdrant</artifactId>
</dependency>
```

2. 创建Qdrant客户端：

```java
@Bean
public QdrantClient qdrantClient() {
    QdrantGrpcClient.Builder grpcClientBuilder = QdrantGrpcClient.newBuilder("127.0.0.1", 6334, false);
    return new QdrantClient(grpcClientBuilder.build());
}
```

3. 创建索引：

```java
var vectorParams = Collections.VectorParams.newBuilder()
        .setDistance(Collections.Distance.Cosine)
        .setSize(1024)
        .build();
qdrantClient.createCollectionAsync("testv", vectorParams);
```

4. 配置Qdrant Embedding Store：

```java
@Bean
public EmbeddingStore<TextSegment> embeddingStore() {
    return QdrantEmbeddingStore.builder()
            .host("127.0.0.1")
            .port(6334)
            .collectionName("testv")
            .build();
}
```

5. 文本生成与存储：

```java
TextSegment segment1 = TextSegment.from("浏览器报错 404，请检测您输入的路径是否正确");
segment1.metadata().put("author", "冷冷");
Embedding embedding1 = embeddingModel.embed(segment1).content();
embeddingStore.add(embedding1, segment1);
```

### 向量查询与过滤

1. 基本向量查询：

```java
Embedding queryEmbedding = embeddingModel.embed("404 是哪里的问题？").content();
EmbeddingSearchRequest embeddingSearchRequest = EmbeddingSearchRequest.builder()
        .queryEmbedding(queryEmbedding)
        .maxResults(1)
        .build();
EmbeddingSearchResult<TextSegment> searchResult = embeddingStore.search(embeddingSearchRequest);
System.out.println(searchResult.matches().get(0).embedded().text());
```

2. 带元数据过滤的查询：

```java
EmbeddingSearchRequest embeddingSearchRequest = EmbeddingSearchRequest.builder()
        .queryEmbedding(queryEmbedding)
        .filter(metadataKey("author").isEqualTo("冷冷"))
        .maxResults(1)
        .build();
```

3. 常用过滤器：

| Filter名称 | 功能 | 使用示例 |
|-----------|------|---------|
| And | 同时满足多个条件 | `Filter.and(condition1, condition2)` |
| Or | 满足其中任意一个条件 | `Filter.or(condition1, condition2)` |
| Not | 不满足条件 | `Filter.not(condition)` |
| IsEqualTo | 等于 | `new IsEqualTo("field", "value")` |
| IsGreaterThan | 大于 | `new IsGreaterThan("field", value)` |
| IsLessThan | 小于 | `new IsLessThan("field", value)` |
| IsIn | 在列表内 | `new IsIn("field", listOfValues)` |

4. 输出结果：

```java
List<EmbeddingMatch<TextSegment>> relevant = searchResult.matches();
EmbeddingMatch<TextSegment> embeddingMatch = relevant.get(0);

System.out.println(embeddingMatch.score());  // 输出匹配分数
System.out.println(embeddingMatch.embedded().text());  // 输出匹配文本
```

## 结论

本文档详细介绍了Embedding模型的概念、LangChain支持的向量数据库、文本向量化过程，以及如何使用Qdrant向量库进行存储和查询。通过这些步骤，你可以快速搭建基于Qdrant的高效向量搜索系统，为自然语言处理任务提供强大的支持。