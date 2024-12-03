---
title: 函数增强搜索
---

[SearchApi](https://www.searchapi.io/) 是一个实时搜索引擎结果页面（SERP）API。你可以使用它进行 Google、Google News、Bing、Bing News、Baidu、Google Scholar 等搜索引擎的查询，获取有机搜索结果。


<img src='https://minio.pigx.top/oss/202410/1728463357.png' alt='1728463357'/>

## 使用方法

### 获取 API KEY

<img src='https://minio.pigx.top/oss/202410/1728397591.png' alt='1728397591'/>

### 依赖配置
在你的项目 `pom.xml` 中添加以下依赖：

```xml
<dependency>
    <groupId>dev.langchain4j</groupId>
  <artifactId>langchain4j-web-search-engine-searchapi</artifactId>
</dependency>

```

### 定义 Ai Service

```java
public interface ChatAssistant {

    @SystemMessage("""
            	1.	搜索支持：你的职责是为用户提供基于网络搜索的支持。
            	2.	事件验证：如果用户提到的事件尚未发生或信息不明确，你需要通过网络搜索确认或查找相关信息。
            	3.	网络搜索请求：使用用户的查询创建网络搜索请求，并通过网络搜索工具进行实际查询。
            	4.	引用来源：在最终回应中，必须包括搜索到的来源链接，以确保信息的准确性和可验证性。
            """)
    String chat(String message);
}
```

### 注入 web search

```java
@Bean
public ChatAssistant chatAssistant(ChatLanguageModel chatLanguageModel) {
    SearchApiWebSearchEngine searchEngine = SearchApiWebSearchEngine.builder()
            .apiKey("p8SZVNAweqTtoZBBTVnXttcj")// 测试使用
            .engine("google")
            .build();

    WebSearchTool webSearchTool = WebSearchTool.from(searchEngine);
    return AiServices.builder(ChatAssistant.class).chatLanguageModel(chatLanguageModel).tools(webSearchTool).build();
}
```

### 测试

```java
String chat = chatAssistant.chat("20241008 上证指数是多少");

System.out.println(chat);

截至2024年10月8日，A股市场迎来了国庆节后的首个交易日，主要指数表现强劲。具体到上证指数，开盘时涨幅达到了10.13%，但之后的走势有所调整，最终收盘时上证指数报收于3489.78点，涨幅为4.59%。这一天，沪深两市的成交额均非常活跃，接近或超过3.5万亿元人民币。

以上信息来源于多个新闻源，包括财新网、观察者网、中国新闻网、新浪财经等，您可以点击提供的链接查看更详细的信息和报道背景。请注意，这些数据和分析仅供参考，市场情况可能会随时变化。

```

### Langchain4j 支持的搜索引擎
| SearchApi 引擎 | 是否支持 |
| --- | --- |
| [Google Web Search](https://www.searchapi.io/docs/google) | ✅ |
| [Google News](https://www.searchapi.io/docs/google-news) | ✅ |
| [Bing](https://www.searchapi.io/docs/bing) | ✅ |
| [Bing News](https://www.searchapi.io/docs/bing-news) | ✅ |
| [Baidu](https://www.searchapi.io/docs/baidu) | ✅ |


任何返回 `organic_results` 数组的搜索引擎都可以被此库支持，即使不在上述列表中，只要有 `title`、`link` 和 `snippet` 字段的有机搜索结果。



