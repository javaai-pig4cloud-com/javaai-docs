---
title: Chat API 上手
---


在这篇文章中，我们将深入了解LangChain4j框架的高层API（AiServices），并展示如何将其与OpenAI集成，以实现简单的聊天功能。我们将讨论LangChain4j支持的各种大型语言模型（LLMs），并逐步展示如何通过示例代码实现。

## LangChain4j支持的LLMs

| 供应商 | 流式调用 | 函数 | JSON  | 多模态 | 观测 |
| --- | --- | --- | --- | --- | --- |
| Amazon Bedrock | ✅ | ✅ |  | text |  |
| Anthropic | ✅ | ✅ |  | text, image |  |
| Azure OpenAI | ✅ | ✅ | ✅ | text, image | ✅ |
| ChatGLM |  |  |  | text |  |
| DashScope | ✅ | ✅ |  | text, image, audio | ✅ |
| GitHub Models | ✅ | ✅ | ✅ | text | ✅ |
| Google AI Gemini |  | ✅ | ✅ | text, image, audio, video, PDF | ✅ |
| Google Vertex AI Gemini | ✅ | ✅ | ✅ | text, image, audio, video, PDF | ✅ |
| Google Vertex AI PaLM 2 |  |  |  | text |  |
| Hugging Face |  |  |  | text |  |
| Jlama | ✅ | ✅ |  | text |  |
| LocalAI | ✅ | ✅ |  | text |  |
| Mistral AI | ✅ | ✅ | ✅ | text |  |
| Ollama | ✅ | ✅ | ✅ | text, image | ✅ |
| OpenAI | ✅ | ✅ | ✅ | text, image | ✅ |
| Qianfan | ✅ | ✅ |  | text |  |
| Cloudflare Workers AI |  |  |  | text |  |
| Zhipu AI | ✅ | ✅ |  | text, image | ✅ |


## LangChain4j的LLM API概述

### 核心：ChatLanguageModel 模型元信息提供

#### 1. 依赖包

在`pom.xml`中添加以下依赖：

```xml
<dependency>
    <groupId>dev.langchain4j</groupId>
    <artifactId>langchain4j</artifactId>
</dependency>
<dependency>
    <groupId>dev.langchain4j</groupId>
    <artifactId>langchain4j-open-ai</artifactId>
</dependency>
```

#### 2. 配置  ChatLanguageModel 提供模型元信息


```java
@Bean
public ChatLanguageModel chatLanguageModel() {
    return OpenAiChatModel.builder()
            .apiKey(System.getenv("DASHSCOPE_KEY"))
            .modelName("qwen-turbo")
            .baseUrl("https://dashscope.aliyuncs.com/compatible-mode/v1")
            .build();
}
```


### 低级LLM API 调用

使用`ChatLanguageModel`接口与大模型进行交互。以下是接口的主要方法：

```java
public interface ChatLanguageModel {
    String generate(String userMessage);
    Response<AiMessage> generate(List<ChatMessage> messages);
}
```

```java
@SpringBootTest
class SimplechatApplicationTest {

    @Autowired
    private ChatLanguageModel chatLanguageModel;

    @Test
    public void testChat(){
        String generate = chatLanguageModel.generate("你好");
        System.out.println(generate);
    }
}
```

### 高级LLM API

为了简化开发，LangChain4j提供了高层API，使开发者能够更专注于业务逻辑，而无需关注底层实现细节。高层API中，`AiService` 用于定义一个集成大模型的服务。

#### 1. 定义AI Service

```java
package com.pig4cloud.ai.service;

/**
 *  AI 助手接口
*/
public interface ChatAssistant {
    String chat(String userMessage);
}
```

-  声明成 Spring Bean， 注入模型

```java
@Bean
public ChatAssistant chatAssistant() {
    return AiServices.builder(ChatAssistant.class)
            .chatLanguageModel(chatLanguageModel())
            .build();
}
```

#### 2. 测试

```java
@SpringBootTest
class ChatAssistantTest {
    @Autowired
    private ChatAssistant chatAssistant;

    @Test
    public void testChat() {
        String message = "Hello";
        String response = chatAssistant.chat(message);
        System.out.println(response);
    }
}
```





