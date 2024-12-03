---
title: Chat 流式输出
---


LangChain4J 是一个强大的库，专门用于与语言学习模型（LLMs）进行交互。其核心功能之一是能够逐个令牌地流式传输来自 LLMs 的响应。这项功能极大地提升了用户体验，使用户可以在模型生成完整响应前，实时获取部分信息。

本文将详细介绍如何使用 LangChain4J 实现流式聊天功能。

## 流式响应处理
### `StreamingResponseHandler` 接口
流式响应的关键接口是 `StreamingResponseHandler`。它允许开发者定义在响应生成过程中的各个事件的处理逻辑。

```java
public interface StreamingResponseHandler<T> {

    void onNext(String token);
 
    default void onComplete(Response<T> response) {}

    void onError(Throwable error);
}
```

### 事件说明

+ **onNext(String token)**：每当生成下一个令牌时触发，通常用于将实时生成的内容及时反馈给前端。
+ **onComplete(Response response)**：当模型生成完成时触发。此时返回一个完整的 `Response` 对象。对于 `StreamingChatLanguageModel`，`T` 为 `AiMessage`；对于 `StreamingLanguageModel`，`T` 为 `String`。
+ **onError(Throwable error)**：当生成过程中发生错误时触发。

## 实现流式聊天的基本示例
以下是使用 `StreamingChatLanguageModel` 实现流式处理的示例：

```java
StreamingChatLanguageModel model = OpenAiStreamingChatModel.builder()
    ...
    .build();

String userMessage = "讲个笑话";

model.generate(userMessage, new StreamingResponseHandler<AiMessage>() {

    @Override
    public void onNext(String token) {
        System.out.println("onNext: " + token);
    }

    @Override
    public void onComplete(Response<AiMessage> response) {
        System.out.println("onComplete: " + response);
    }

    @Override
    public void onError(Throwable error) {
        error.printStackTrace();
    }
});
```

### 示例说明
1. **模型初始化**：通过 `OpenAiStreamingChatModel.builder()` 创建一个流式模型实例，并从环境变量中获取 API 密钥。
2. **用户输入**：定义用户输入消息，此处为“讲个笑话”。
3. **处理响应**：传递实现了 `StreamingResponseHandler` 的匿名类，分别定义 `onNext`、`onComplete` 和 `onError` 的处理逻辑。

## 使用 `TokenStream` 进行流式处理
除了 `StreamingResponseHandler`，您还可以使用 `TokenStream` 逐个令牌流式处理响应。

### 示例代码
```java
interface Assistant {

    TokenStream chat(String message);
}

StreamingChatLanguageModel model = OpenAiStreamingChatModel.builder()
    ...
    .build();

Assistant assistant = AiServices.create(Assistant.class, model);

TokenStream tokenStream = assistant.chat("讲个笑话");

tokenStream.onNext(System.out::println)
    .onComplete(System.out::println)
    .onError(Throwable::printStackTrace)
    .start();
```

### 示例说明
1. **接口定义**：`Assistant` 接口定义了 `chat` 方法，该方法返回 `TokenStream`。
2. **模型初始化**：同样地，通过 `OpenAiStreamingChatModel.builder()` 初始化模型。
3. **TokenStream 处理**：对返回的 `TokenStream` 进行订阅，分别处理 `onNext`、`onComplete` 和 `onError` 事件，并启动流式处理。

## 使用 `Flux` 进行流式处理
除了 `TokenStream`，您还可以通过 Reactor 库中的 `Flux<String>` 实现响应流式传输。为此，您需要引入 `langchain4j-reactor` 依赖。

### Maven 依赖

```xml
<dependency>
    <groupId>dev.langchain4j</groupId>
    <artifactId>langchain4j-reactor</artifactId>
    <version>0.35.0</version>
</dependency>
```

### 示例代码
```java
interface Assistant {

  Flux<String> chat(String message);
}

StreamingChatLanguageModel model = OpenAiStreamingChatModel.builder()
    ...
    .build();

Assistant assistant = AiServices.create(Assistant.class, model);

Flux<String> tokenFlux = assistant.chat("讲个笑话");

tokenFlux.subscribe(
    System.out::println,  // onNext
    Throwable::printStackTrace,  // onError
    () -> System.out.println("onComplete")  // onComplete
);
```

### 示例说明

1. **接口定义**：`Assistant` 接口定义了返回 `Flux<String>` 的 `chat` 方法。
2. **模型初始化**：使用与之前相同的方式初始化模型。
3. **订阅处理**：使用 `Flux.subscribe` 来处理每个生成的令牌、错误和完成事件。

## 总结
LangChain4J 提供了一种高效且灵活的方式来流式传输语言模型的响应。通过 `StreamingResponseHandler`、`TokenStream` 或 `Flux`，开发者可以实现流畅的实时响应体验，从而提升应用的互动性和响应速度。

流式处理让用户无需等待完整响应生成即可获取部分内容，尤其适用于聊天机器人和交互式 AI 应用的开发。

