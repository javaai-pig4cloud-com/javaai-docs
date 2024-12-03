---
title: RAG 结果重排
---


<img src='https://minio.pigx.top/oss/202410/1728463069.png' alt='1728463069'/>


## RRF

### 基本概念

Reciprocal Rank Fusion (RRF) 是一种用于结合多个排序结果的简单而有效的算法。它通过计算每个候选项在多个列表中的排名倒数，然后将这些倒数相加，从而得出一个“融合分数”，并根据该分数对候选项进行重新排序。

### 示例

假设你和三个朋友在寻找一本丢失的书，每个人列出了最有可能找到书的地点，并按从高到低的顺序进行排序。RRF 就是结合这些排序结果，帮助找到最有可能的地点。

#### 列表数据

- **朋友A的列表：**
  1. 书架
  2. 桌子
  3. 床下

- **朋友B的列表：**
  1. 床下
  2. 书架
  3. 桌子

- **朋友C的列表：**
  1. 桌子
  2. 书架
  3. 床下

#### RRF 计算过程

我们为每个地点计算在每个列表中的排名倒数，然后将这些倒数相加，得到融合分数。

1. **书架**
   - 在朋友A的列表中排名第1：$ \frac{1}{1} = 1$
   - 在朋友B的列表中排名第2：$ \frac{1}{2} = 0.5$
   - 在朋友C的列表中排名第2：$ \frac{1}{2} = 0.5$
   - **总分：** $1 + 0.5 + 0.5 = 2$

2. **床下**
   - 在朋友A的列表中排名第3：$ \frac{1}{3} = 0.33$
   - 在朋友B的列表中排名第1：$ \frac{1}{1} = 1$
   - 在朋友C的列表中排名第3：$ \frac{1}{3} = 0.33$
   - **总分：** $0.33 + 1 + 0.33 = 1.66$

3. **桌子**
   - 在朋友A的列表中排名第2：$ \frac{1}{2} = 0.5$
   - 在朋友B的列表中排名第3：$ \frac{1}{3} = 0.33$
   - 在朋友C的列表中排名第1：$ \frac{1}{1} = 1$
   - **总分：** $0.5 + 0.33 + 1 = 1.83$

#### 排序结果

最后，我们根据每个地点的融合分数排序：

- **书架**: 2
- **桌子**: 1.83
- **床下**: 1.66

因此，书架是最有可能找到书的地点。


这个例子清楚地展示了RRF如何结合多个列表进行排序，从而提高结果的精确性。这种方法常用于信息检索和文档重排序中。

### Reranker

重排序模型的核心是计算用户查询与候选文档之间的语义匹配度，并根据该匹配度对结果进行重新排序。通过这种方式，语义排序的效果能够得到显著提升。它的原理是对每个候选文档计算与用户查询的相关性分数，并按相关性高低输出排序后的文档列表。

![RAG Reranking Process](https://minio.pigx.top/oss/202410/1728447436.png)

Jina AI提供了一个强大的reranker模型，可以轻松集成到LangChain4j项目中。以下是使用Jina Reranker的基本步骤。

#### Maven 依赖

在你的Maven项目中添加以下依赖：

```xml
<dependency>
    <groupId>dev.langchain4j</groupId>
    <artifactId>langchain4j-jina</artifactId>
</dependency>
```

#### 基本用法

以下是在LangChain4j中使用Jina Reranker的基本示例：

```java
// 创建Jina评分模型
ScoringModel scoringModel = JinaScoringModel.builder()
    .apiKey(System.getenv("JINA_API_KEY"))
    .modelName("jina-reranker-v2-base-multilingual")
    .build();

// 创建内容聚合器
ContentAggregator contentAggregator = ReRankingContentAggregator.builder()
    .scoringModel(scoringModel)
    // 可以添加其他配置选项
    .build();

// 创建检索增强器
RetrievalAugmentor retrievalAugmentor = DefaultRetrievalAugmentor.builder()
    // 添加其他必要的配置
    .contentAggregator(contentAggregator)
    .build();

// 构建AI服务
Assistant assistant = AiServices.builder(Assistant.class)
    .chatLanguageModel(/* 配置你的语言模型 */)
    .retrievalAugmentor(retrievalAugmentor)
    .build();
```

#### 关键组件说明

1. **JinaScoringModel**: Jina Reranker的核心组件，需要API密钥和模型名称。
2. **ReRankingContentAggregator**: 使用评分模型来重新排序检索到的内容。
3. **RetrievalAugmentor**: 整合检索和重新排序过程的高级组件。
4. **AiServices**: LangChain4j的工具类，用于构建集成了各种功能的AI服务。

#### 注意事项

- 设置`JINA_API_KEY`环境变量。
- 选择适合任务的Jina模型。
- ReRankingContentAggregator和RetrievalAugmentor可能需要额外配置。

#### 进阶使用

1. 调整重新排序的参数，如考虑的结果数量。
2. 结合其他检索技术，如向量搜索。
3. 实现自定义的评分逻辑。

## RRF vs Reranker 比较

| 特点           | Reciprocal Rank Fusion (RRF)          | 重排序 (Rerank)                    |
|----------------|---------------------------------------|-------------------------------------|
| **目的**       | 融合来自多个源的结果                  | 对初步结果进行重新排序              |
| **方法**       | 计算排名倒数并累加                    | 使用模型评估相关性并调整顺序        |
| **实现复杂度** | 相对简单                              | 依赖特定模型，复杂度较高            |
| **适用场景**   | 多源数据融合                          | 结果优化和精细化处理                |

## 结论

RRF和Reranker是两种不同但互补的技术。RRF更适合于多源数据的融合，而Reranker则专注于提高单一查询结果集的质量和相关性。在实际应用中，可以根据具体需求选择适当的方法，或将两者结合使用以达到更好的信息检索效果。通过集成像Jina Reranker这样的工具到LangChain4j项目中，可以显著提高检索结果的质量，这对于构建高性能的问答系统、搜索引擎或任何需要精确信息检索的应用程序都是非常有价值的。