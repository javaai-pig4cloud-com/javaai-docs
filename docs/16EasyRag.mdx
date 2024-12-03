---
title: RAG Easy 快速上手
---

## 什么是 RAG？

检索增强生成（Retrieval-Augmented Generation，简称RAG）是一种结合大型语言模型（LLM）和外部知识库的技术，旨在提高生成文本的准确性和相关性。以下是对RAG的通俗介绍：
RAG的基本概念
RAG的核心思想是通过引入外部知识源来增强LLM的输出能力。传统的LLM通常基于其训练数据生成响应，但这些数据可能过时或不够全面。RAG允许模型在生成答案之前，从特定的知识库中检索相关信息，从而提供更准确和上下文相关的回答

## RAG 流程
RAG 过程分为两个阶段：索引（indexing）和检索（retrieval）。LangChain4j 提供了这两个阶段的工具。

### 索引阶段
在索引阶段，文档经过预处理以便在检索阶段进行高效搜索。对于向量搜索，通常包括清理文档、添加额外数据和元数据、将文档分割为小段（分块），将这些段落嵌入为向量，并存储在嵌入存储（向量数据库）中。

索引通常是离线进行的，可以通过定期任务（如每周重建索引）完成。

<img src='https://minio.pigx.top/oss/202410/1728455181.png' alt='1728455181'/>
### 检索阶段

检索阶段通常是在线进行的，当用户提交问题时，从索引的文档中寻找相关信息。对于向量搜索来说，这通常包括将用户的查询嵌入为向量，并在嵌入存储中执行相似性搜索，找到相关的段落并将它们注入提示中，再发送给 LLM。

<img src='https://minio.pigx.top/oss/202410/1728455302.png' alt='1728455302'/>

## Easy RAG
LangChain4j 提供了“Easy RAG”功能，旨在让你快速上手 RAG，无需学习嵌入、选择向量存储或如何解析和分割文档等复杂步骤。只需指向你的文档，LangChain4j 将为你处理大部分细节。

#### 1. 导入依赖：

```xml
<dependency>
    <groupId>dev.langchain4j</groupId>
    <artifactId>langchain4j-easy-rag</artifactId>
</dependency>
```

#### 2. 配置存储和Ai service 

```java
/**
    * 嵌入存储 (简易内存存储)
    *
    * @return {@link InMemoryEmbeddingStore }<{@link TextSegment }>
    */
@Bean
public InMemoryEmbeddingStore<TextSegment> embeddingStore() {
    return new InMemoryEmbeddingStore<>();
}


@Bean
public ChatAssistant assistant(ChatLanguageModel chatLanguageModel, EmbeddingStore<TextSegment> embeddingStore) {
    return AiServices.builder(ChatAssistant.class)
            .chatLanguageModel(chatLanguageModel)
            .chatMemory(MessageWindowChatMemory.withMaxMessages(10))
            .contentRetriever(EmbeddingStoreContentRetriever.from(embeddingStore))
            .build();
}
```

#### 3. 向量存储文档

```java
Document document = FileSystemDocumentLoader.loadDocument("/Users/lengleng/Downloads/test.docx");
EmbeddingStoreIngestor.ingest(document,embeddingStore);
```

#### 4. 测提提问

```java
String result = assistant.chat("合同总金额");
```

## 进阶配置

```java
/**
 * 这个类负责将文档摄入嵌入存储。
 * 它使用各种组件来转换、分割和嵌入文档，然后存储它们。
 */
public class EmbeddingStoreIngestor {

    // 将输入文档转换为适合处理的格式
    private final DocumentTransformer documentTransformer;

    // 将文档分割成更小的段落
    private final DocumentSplitter documentSplitter;

    // 转换单个文本段落（例如，用于标准化或清理）
    private final TextSegmentTransformer textSegmentTransformer;

    // 为文本段落生成嵌入向量
    private final EmbeddingModel embeddingModel;

    // 存储生成的嵌入向量及其对应的文本段落
    private final EmbeddingStore<TextSegment> embeddingStore;
}

// 使用构建器模式的示例
EmbeddingStoreIngestor
    .builder()
    .documentTransformer()  // 设置文档转换器
    .documentSplitter()     // 设置文档分割器
    .embeddingModel()       // 设置嵌入模型
    .embeddingStore()       // 设置嵌入存储
    .build()                // 构建EmbeddingStoreIngestor实例
    .ingest(document);      // 将文档摄入嵌入存储
```