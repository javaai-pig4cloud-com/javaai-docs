---
title:  业务动态 JSON 结构化
---

## 1. **定义基础的JSON Schema**

首先，需要定义一个基础的JSON Schema结构。`LangChain4j`支持动态生成和调整这些结构，以适应不同业务需求。每个Schema可以包含多种数据类型（如字符串、数组、整数等），并且通过键值对的形式进行定义。

```java
public JsonSchema createDynamicJsonSchema(Map<String, JsonSchemaType> properties) {
    return JsonSchema.builder()
            .rootElement(JsonObjectSchema.builder()
                    .properties(properties)
                    .build())
            .build();
}
```

在这里，`properties`是一个`Map`，键为JSON字段名，值为字段的类型（如字符串、整数等）。可以根据业务需求设置不同字段类型，例如：

```java
Map<String, JsonSchemaType> properties = new HashMap<>();
properties.put("invoiceNumber", JsonSchemaType.JSON_STRING_SCHEMA);
properties.put("amount", JsonSchemaType.JSON_NUMBER_SCHEMA);
```


## 2. **将JSON Schema集成到请求中**
生成了相应的JSON Schema后，可以将其嵌入到`ChatRequest`中，控制输出格式。

```java
public void processChatWithDynamicSchema( String inputText) {
    OpenAiChatModel chatModel = OpenAiChatModel.builder()
            .strictJsonSchema(true)  // 强制输出符合schema的格式
            .build();

    // 动态生成JSON Schema
    JsonSchema dynamicSchema = buildSchemaForBusiness(businessType);

    ResponseFormat responseFormat = ResponseFormat.builder()
            .type(ResponseType.JSON)  // 设置为JSON输出格式
            .jsonSchema(createDynamicJsonSchema)  // 应用动态生成的Schema
            .build();

    ChatRequest chatRequest = ChatRequest.builder()
            .messages(UserMessage.from(
                    TextContent.from(inputText)
            ))
            .responseFormat(responseFormat)
            .build();

    ChatResponse response = chatModel.chat(chatRequest);
    System.out.println(response.aiMessage().text());
}
```


## 3. **实际使用示例**
假设我们有一个业务场景需要处理OCR文本和发票信息，可以通过调用`processChatWithDynamicSchema`来动态设置Schema。例如：

```java
// 处理发票信息场景
processChatWithDynamicSchema("Please analyze the following invoice.");
```

通过这种方式，不同业务场景下的Schema可以动态生成并控制输出格式，保证了API的灵活性和统一性。


这一方案能够灵活应对各种业务场景，并通过LangChain4j动态生成和控制输出的JSON格式，提升了开发效率。