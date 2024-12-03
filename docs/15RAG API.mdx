---
title: RAG API 基础
---

LangChain4j 是一个强大的 Java 库,提供了丰富的 API 来简化构建自定义 RAG(检索增强生成)管道的过程。本指南将详细介绍 LangChain4j 的主要组件和 API,从简单到复杂的多种管道实现。


<img src='https://minio.pigx.top/oss/202410/1728455030.png' alt='1728455030'/>

## 2. 核心概念

### 2.1 Document (文档)

`Document` 类表示一个完整的文档,例如单个 PDF 文件或网页。

#### 主要方法:
- `Document.text()`: 返回文档的文本内容
- `Document.metadata()`: 返回文档的元数据
- `Document.toTextSegment()`: 将 `Document` 转换为 `TextSegment`
- `Document.from(String, Metadata)`: 从文本和元数据创建 `Document`
- `Document.from(String)`: 从文本创建不带元数据的 `Document`

### 2.2 Metadata (元数据)

`Metadata` 存储文档的额外信息,如名称、来源、最后更新时间等。

#### 主要方法:
- `Metadata.from(Map)`: 从 `Map` 创建 `Metadata`
- `Metadata.put(String key, String value)`: 添加元数据条目
- `Metadata.getString(String key)` / `getInteger(String key)`: 获取指定类型的元数据值
- `Metadata.containsKey(String key)`: 检查是否包含指定键
- `Metadata.remove(String key)`: 移除指定键的元数据条目
- `Metadata.copy()`: 复制元数据
- `Metadata.toMap()`: 将元数据转换为 `Map`

### 2.3 TextSegment (文本片段)

`TextSegment` 表示文档的一个片段,专用于文本信息。

#### 主要方法:
- `TextSegment.text()`: 返回文本片段的内容
- `TextSegment.metadata()`: 返回文本片段的元数据
- `TextSegment.from(String, Metadata)`: 从文本和元数据创建 `TextSegment`
- `TextSegment.from(String)`: 从文本创建不带元数据的 `TextSegment`

### 2.4 Embedding (嵌入)

`Embedding` 类封装了一个数值向量,表示嵌入内容的语义含义。

#### 主要方法:
- `Embedding.dimension()`: 返回嵌入向量的维度
- `CosineSimilarity.between(Embedding, Embedding)`: 计算两个嵌入向量的余弦相似度
- `Embedding.normalize()`: 对嵌入向量进行归一化

## 3. 文档处理

### 3.1 Document Loader (文档加载器)

LangChain4j 提供了多种文档加载器:
- `FileSystemDocumentLoader`: 从文件系统加载文档
- `UrlDocumentLoader`: 从 URL 加载文档
- `AmazonS3DocumentLoader`: 从 Amazon S3 加载文档
- `AzureBlobStorageDocumentLoader`: 从 Azure Blob 存储加载文档
- `GitHubDocumentLoader`: 从 GitHub 仓库加载文档
- `TencentCosDocumentLoader`: 从腾讯云 COS 加载文档

### 3.2 Document Parser (文档解析器)

用于解析不同格式的文档:
- `TextDocumentParser`: 解析纯文本文件
- `ApachePdfBoxDocumentParser`: 解析 PDF 文件
- `ApachePoiDocumentParser`: 解析 MS Office 文件格式
- `ApacheTikaDocumentParser`: 自动检测并解析几乎所有文件格式

示例:
```java
// 加载单个文档
Document document = FileSystemDocumentLoader.loadDocument("/path/to/file.txt", new TextDocumentParser());

// 加载目录下的所有文档
List<Document> documents = FileSystemDocumentLoader.loadDocuments("/path/to/directory", new TextDocumentParser());
```

### 3.3 Document Transformer (文档转换器)

`DocumentTransformer` 用于对文档执行各种转换,如清理、过滤、增强或总结。

目前提供的转换器:
- `HtmlToTextDocumentTransformer`: 从 HTML 中提取文本内容和元数据

### 3.4 Document Splitter (文档拆分器)

用于将文档拆分成更小的片段:
- `DocumentByParagraphSplitter`: 按段落拆分
- `DocumentBySentenceSplitter`: 按句子拆分
- `DocumentByWordSplitter`: 按单词拆分
- `DocumentByCharacterSplitter`: 按字符拆分
- `DocumentByRegexSplitter`: 按正则表达式拆分

使用步骤:
1. 实例化 `DocumentSplitter` 并指定 `TextSegment` 的大小和重叠字符数
2. 调用 `split(Document)` 或 `splitAll(List<Document>)` 方法
3. `DocumentSplitter` 将文档拆分成小片段,并组合为 `TextSegment`

## 4. 嵌入处理

### 4.1 Embedding Model (嵌入模型)

`EmbeddingModel` 接口表示一种将文本转换为 `Embedding` 的模型。

#### 主要方法:
- `EmbeddingModel.embed(String)`: 嵌入指定文本
- `EmbeddingModel.embed(TextSegment)`: 嵌入指定 `TextSegment`
- `EmbeddingModel.embedAll(List<TextSegment>)`: 嵌入多个 `TextSegment`
- `EmbeddingModel.dimension()`: 返回嵌入向量的维度

### 4.2 Embedding Store (嵌入存储)

`EmbeddingStore` 接口表示一个嵌入存储库(向量数据库),用于存储和高效搜索相似的嵌入。

#### 主要方法:
- `EmbeddingStore.add(Embedding)`: 添加嵌入并返回随机 ID
- `EmbeddingStore.addAll(List<Embedding>)`: 添加多个嵌入并返回随机 ID 列表
- `EmbeddingStore.search(EmbeddingSearchRequest)`: 搜索最相似的嵌入
- `EmbeddingStore.remove(String id)`: 删除指定 ID 的嵌入

### 4.3 Embedding Store Ingestor (嵌入存储摄取器)

`EmbeddingStoreIngestor` 负责将文档嵌入并存储到 `EmbeddingStore` 中。

示例:
```java
EmbeddingStoreIngestor ingestor = EmbeddingStoreIngestor.builder()
    .embeddingModel(embeddingModel)
    .embeddingStore(embeddingStore)
    .build();

ingestor.ingest(document1);
```

可以通过指定 `DocumentTransformer` 和 `DocumentSplitter`,在嵌入前对文档进行转换和拆分。

## 5. 构建 RAG 管道

使用 LangChain4j 构建 RAG 管道的一般步骤:

1. 加载文档: 使用适当的 `DocumentLoader` 和 `DocumentParser` 加载文档
2. 转换文档: 使用 `DocumentTransformer` 清理或增强文档(可选)
3. 拆分文档: 使用 `DocumentSplitter` 将文档拆分为更小的片段
4. 嵌入文档: 使用 `EmbeddingModel` 将文档片段转换为嵌入向量
5. 存储嵌入: 使用 `EmbeddingStore` 存储嵌入向量
6. 检索相关内容: 根据用户查询,从 `EmbeddingStore` 检索最相关的文档片段
7. 生成响应: 将检索到的相关内容与用户查询一起提供给语言模型,生成最终响应

## 6. 最佳实践

- 根据具体需求选择合适的文档拆分策略
- 使用自定义的 `DocumentTransformer` 来清理和增强文档
- 选择合适的嵌入模型和嵌入存储以平衡性能和准确性
- 定期更新和维护嵌入存储,以确保信息的时效性
- 对检索结果进行后处理,如重新排序或过滤,以提高相关性

## 7. 结语

LangChain4j 提供了构建高效 RAG 系统所需的全套工具。通过灵活组合这些组件,您可以创建适合特定用例的自定义 RAG 管道。随着项目的发展,不断优化和调整各个组件,以提高系统的整体性能和准确性。