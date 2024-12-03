---
title: API 进阶配置
---


### 1. 日志配置 (Logging)
LangChain4j 使用 SLF4J 作为日志接口，支持集成各种日志后端，如 Logback 或 Log4j。

#### 纯 Java 环境
要启用对每个请求和响应的日志记录，可以在创建模型实例时通过以下方式设置：

```java
OpenAiChatModel.builder()
    ...
    .logRequests(true)    // 启用请求日志
    .logResponses(true)   // 启用响应日志
    .build();
```

确保在依赖项中包含 SLF4J 的日志后端，比如 Logback

#### Spring Boot 环境

在 Spring Boot 集成中，可以通过 `application.properties` 文件配置日志级别：

> **只有日志级别调整为debug级别，同时配置以上 langchain 日志输出开关才有效**

```yaml
logging:
  level:
    root: debug
```

### 2. 监控 (Observability)
LangChain4j 提供了一些语言模型（如 `ChatLanguageModel` 和 `StreamingChatLanguageModel`），支持通过 `ChatModelListener` 监听以下事件：

+ 请求到达 LLM
+ LLM 返回的响应
+ 错误处理

事件监听的例子如下：

```java
ChatModelListener listener = new ChatModelListener() {

    @Override
    public void onRequest(ChatModelRequestContext requestContext) {
        ChatModelRequest request = requestContext.request();
        Map<Object, Object> attributes = requestContext.attributes();
        // 记录请求
    }

    @Override
    public void onResponse(ChatModelResponseContext responseContext) {
        ChatModelResponse response = responseContext.response();
        ChatModelRequest request = responseContext.request();
        Map<Object, Object> attributes = responseContext.attributes();
        // 记录响应
    }

    @Override
    public void onError(ChatModelErrorContext errorContext) {
        Throwable error = errorContext.error();
        ChatModelRequest request = errorContext.request();
        ChatModelResponse partialResponse = errorContext.partialResponse();
        Map<Object, Object> attributes = errorContext.attributes();
        // 记录错误
    }
};

ChatLanguageModel model = OpenAiChatModel.builder()
        ...
        .listeners(List.of(listener))  // 添加监听器
        .build();
```

### 3. 重试机制 (Retry Configuration)
LangChain4j 支持重试配置，可用于处理失败的请求。

可以通过 `maxRetries` 来配置重试逻辑，指定重试次数和延迟等参数：

```java
ChatLanguageModel model = OpenAiChatModel.builder()
    ...
    .maxRetries(5)  // 设置重试策略
    .build();
```

### 4. 超时配置 (Timeout Configuration)
对于超时配置，可以通过 `timeout` 设置请求的超时时间：

```java
ChatLanguageModel model = OpenAiChatModel.builder()
    ...
    .timeout(Duration.ofSeconds(10)) // 设置10秒超时
    .build();
```

