---
title: RAG API 增强
---

<img src='https://minio.pigx.top/oss/202410/1728458493.png' alt='1728458493'/>

### 检索增强器（Retrieval Augmentor）

`RetrievalAugmentor` 是 RAG（检索增强生成）流程的核心，它通过从不同的数据源中检索相关内容来增强用户的消息。

在创建 AI service 时，可以指定 `RetrievalAugmentor` 实例：

```java

@Bean
public ChatAssistant assistant(ChatLanguageModel chatLanguageModel, EmbeddingStore<TextSegment> embeddingStore) {

    DefaultRetrievalAugmentor retrievalAugmentor = DefaultRetrievalAugmentor.builder()
            .queryTransformer()  // 查询增强
            .contentRetriever() // 内容源 单个直接配置
            .queryRouter(new DefaultQueryRouter())// 多个内容源，路由
            .contentAggregator() // 匹配结果聚合
            .contentInjector()   // 结果提示词注入
            .executor()  // 并行化
            .build();

    return AiServices.builder(ChatAssistant.class)
            .chatLanguageModel(chatLanguageModel)
            .chatMemory(MessageWindowChatMemory.withMaxMessages(10))
            .retrievalAugmentor(retrievalAugmentor)
            .build();
}
```

每次调用 AI 服务时，都会自动使用这个增强器来处理当前的用户消息。你可以使用默认的增强器实现，也可以根据需求自定义。

### 默认检索增强器

LangChain4j 提供了开箱即用的 `RetrievalAugmentor` 实现：`DefaultRetrievalAugmentor`。它适用于大多数的 RAG 场景。这个实现的灵感来源于 [LangChain 博客文章](https://blog.langchain.dev/deconstructing-rag) 和 [相关论文](https://arxiv.org/abs/2312.10997)。

### 查询（Query）

`Query` 代表用户的查询请求，包含查询的文本以及相关的元数据。

#### 查询元数据

`Query` 中的 `Metadata` 包含在 RAG 流程中有用的上下文信息，例如：
- `Metadata.userMessage()`：表示用户输入的原始消息。
- `Metadata.chatMemoryId()`：一个用于标识用户的ID，可以应用在数据访问限制或过滤上。
- `Metadata.chatMemory()`：之前的所有对话消息，用于理解查询的上下文。

### 查询转换器（Query Transformer）

`QueryTransformer` 用于将原始查询转换为一个或多个新的查询，以提高检索的准确性。常见的查询优化方式包括：
- 查询压缩：压缩冗长的对话，生成一个简明的查询。
- 查询扩展：将简单的查询扩展为多个相关的查询。
- 查询重写：对查询进行改写，使其更适合检索。

**示例：**
```java
QueryTransformer transformer = new CompressingQueryTransformer();
```

#### 默认查询转换器

`DefaultQueryTransformer` 是最简单的实现，它直接传递原始查询而不进行任何修改。

#### 压缩查询转换器

`CompressingQueryTransformer` 使用大语言模型（LLM）压缩查询和对话上下文，生成一个更简洁、独立的查询。例如：

```
用户：告诉我关于John Doe的信息。
AI：John Doe 是一个著名作家。
用户：他住在哪里？
```
对于“他住在哪里？”这样的查询，`CompressingQueryTransformer` 会自动转换为“John Doe 住在哪里？”，以便更精准地检索信息。

#### 扩展查询转换器

`ExpandingQueryTransformer` 可以将简单的查询扩展为多个不同的表达方式，从而提高相关内容的覆盖面。

### 内容（Content）

`Content` 代表系统从数据源中检索到的与查询相关的内容。目前支持的主要是文本内容（`TextSegment`），未来可能会扩展支持其他模态，如图像、音频、视频等。

### 内容检索器（Content Retriever）

`ContentRetriever` 根据用户的查询从底层数据源中获取内容，数据源可以是：
- 嵌入向量存储
- 全文搜索引擎
- 向量与全文检索结合
- 网络搜索引擎
- SQL数据库
- 知识图谱等

#### 嵌入存储内容检索器

`EmbeddingStoreContentRetriever` 使用嵌入模型将查询转化为向量，并从嵌入存储中检索相关的内容。

**示例代码：**
```java
EmbeddingStore embeddingStore = ...
EmbeddingModel embeddingModel = ...

ContentRetriever contentRetriever = EmbeddingStoreContentRetriever.builder()
    .embeddingStore(embeddingStore)
    .embeddingModel(embeddingModel)
    .maxResults(3)   // 返回最多3条结果
    .dynamicMaxResults(query -> 3)  // 根据查询动态指定maxResults
    .minScore(0.75)  // 过滤分数低于0.75的内容
    .dynamicMinScore(query -> 0.75)  // 根据查询动态指定minScore
    .filter(metadataKey("userId").isEqualTo("12345"))  // 过滤指定用户的内容
    .dynamicFilter(query -> {
        String userId = getUserId(query.metadata().chatMemoryId());
        return metadataKey("userId").isEqualTo(userId);  // 动态过滤
    })
    .build();
```

#### 网络搜索内容检索器

`WebSearchContentRetriever` 通过 `WebSearchEngine` 从互联网上检索相关内容。

**示例代码：**
```java
WebSearchEngine googleSearchEngine = GoogleCustomWebSearchEngine.builder()
    .apiKey(System.getenv("GOOGLE_API_KEY"))
    .csi(System.getenv("GOOGLE_SEARCH_ENGINE_ID"))
    .build();

ContentRetriever contentRetriever = WebSearchContentRetriever.builder()
    .webSearchEngine(googleSearchEngine)
    .maxResults(3)
    .build();
```
查看完整示例请参考[这里](https://github.com/langchain4j/langchain4j-examples/blob/main/rag-examples/src/main/java/_3_advanced/_08_Advanced_RAG_Web_Search_Example.java)。

#### SQL数据库内容检索器

`SqlDatabaseContentRetriever` 是用于从SQL数据库检索数据的实验性实现。更多信息可参考相关javadoc文档。

#### Azure AI 搜索内容检索器

`AzureAiSearchContentRetriever` 在 `langchain4j-azure-ai-search` 模块中可用。

#### Neo4j内容检索器

`Neo4jContentRetriever` 可用于从Neo4j数据库中检索与查询相关的内容。

### 查询路由器（Query Router）

`QueryRouter` 负责将查询分配到合适的内容检索器。

#### 默认查询路由器

`DefaultQueryRouter` 将每个查询路由到所有配置的内容检索器。

#### 语言模型查询路由器

`LanguageModelQueryRouter` 使用大语言模型（LLM）决定应该将查询发送到哪个检索器。

### 并行化处理

当只有一个查询和一个检索器时，`DefaultRetrievalAugmentor` 会在单线程中执行查询和检索。否则，它会使用 `Executor` 并行处理多个查询和检索任务。默认情况下，系统会使用一个修改后的 `Executors.newCachedThreadPool()` 来实现这一功能，你也可以提供自定义的 `Executor`：
```java
DefaultRetrievalAugmentor augmentor = DefaultRetrievalAugmentor.builder()
    .executor(executor)
    .build();
```