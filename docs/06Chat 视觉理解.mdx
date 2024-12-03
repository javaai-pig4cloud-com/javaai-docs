---
title: Chat 视觉理解
---


### 示例代码：基于Dashscope的LangChain4j视觉理解

这个示例展示了如何通过Dashscope的API，结合LangChain4j进行图像理解。使用的模型是`qwen-vl-max`，其支持视觉-语言的多模态任务。 

> 从非规则图片中读取指定日期的指数点数


<img src='https://minio.pigx.top/oss/202410/1728291870.png' alt='1728291870'/>

#### 构建大模型客户端

```java
@Bean
public ChatLanguageModel chatLanguageModel() {
return OpenAiChatModel.builder()
        .apiKey(System.getenv("DASHSCOPE_KEY"))
        .modelName("qwen-vl-max")  // 设置使用的模型名称
        .baseUrl("https://dashscope.aliyuncs.com/compatible-mode/v1")
        .build();
}
```


####  构建 ImageContent

```java

/**
 * 作者: lengleng
 * 视觉理解示例 - 通过Dashscope进行图像分析
 */
@SpringBootTest
class LLMConfigTest {
    @Autowired
    private ChatLanguageModel chatLanguageModel;

    @Value("1.png")
    private Resource resource;

    @Test
    void chatLanguageModel() throws IOException {

        byte[] byteArray = resource.getContentAsByteArray();
        String encodeToString = Base64.getEncoder().encodeToString(byteArray);

        UserMessage userMessage = UserMessage.from(
                TextContent.from("提取图片中 9月30号的上证指数点数")
                ,
                ImageContent.from(encodeToString, "image/png")
        );
        Response<AiMessage> response = chatLanguageModel.generate(userMessage);
        System.out.println(response.content().text());
    }
}
```

### 说明：
1. **模型选择**：`qwen-vl-max` 是一个多模态大模型，支持图片和文本的结合输入，适用于视觉-语言任务。
2. **图片上传**：通过`Base64`编码将图片转化为字符串，结合`ImageContent`和`TextContent`一起发送到模型进行处理。
3. **API调用**：使用`OpenAiChatModel`来构建请求，并通过`chat()`方法调用模型。请求内容包括文本提示和图片，模型会根据输入返回分析结果。
4. **解析与输出**：从`ChatResponse`中获取AI的回复，打印出处理后的结果。

### 应用场景：
+ **图像文字提取**：如发票信息的提取、表单中的数据信息识别等。
+ **图像标注和理解**：结合文本输入，根据特定位置或内容要求对图像进行详细分析。

这种方法可以应用在实际业务中，如OCR（光学字符识别）、图像审核、合规性检查等。

