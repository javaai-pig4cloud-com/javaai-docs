---
title: JSON 结构化输出
---


在与大语言模型(LLM)交互时,我们常常需要将其输出转换为结构化的数据格式,以便进一步处理和使用。LangChain4j框架为我们提供了一种优雅的方式来实现这一目标。本文将深入探讨LangChain4j如何将LLM的返回结果格式化为各种数据类型,包括基本类型、集合、自定义POJO等。

## LangChain4j支持的返回类型


| 序号 | 类型分类            | 支持的类型                                         |
| ---- | ------------------- | ------------------------------------------------ |
| 1    | 字符串 (String)      | String                                           |
| 2    | 基本类型            | boolean, byte, short, int, long, float, double   |
| 3    | 包装类型            | Boolean, Byte, Short, Integer, Long, Float, Double, BigDecimal |
| 4    | 时间类型            | Date, LocalDate, LocalTime, LocalDateTime        |
| 5    | 集合类型            | List, Set                                        |
| 6    | 枚举类型            | Enum                                             |
| 7    | 自定义POJO          | 自定义的Java类                                    |
| 8    | 自定义Result        | 自定义的Result类型                                |
| 9    | AI消息类型          | AiMessage                                        |


## 结构化输出示例
让我们通过一些具体的例子来看看如何使用LangChain4j处理不同类型的输出。

### 布尔值与枚举
```java
package com.pig4cloud.ai.sentiment;

import dev.langchain4j.service.UserMessage;
import dev.langchain4j.service.spring.AiService;

public interface SentimentAnalyzer {
    
    // text=假期结束开始上班
    @UserMessage("{{it}} 是否具有正面情感？")
    boolean isPositive(String text);

    // text=假期结束开始上班
    @UserMessage("分析 {{it}} 的情感")
    Sentiment analyzeSentimentOf(String text);

    enum Sentiment {
        POSITIVE, // 正面情感
        NEGATIVE, // 负面情感
        NEUTRAL   // 中立情感
    }
}

```

在这个例子中,我们定义了一个`SentimentAnalyzer`接口,它使用LangChain4j的`@AiService`和`@UserMessage`注解来处理情感分析任务。该接口包含两个方法:

+ `isPositive`: 返回布尔值,表示文本是否具有积极情感。
+ `analyzeSentimentOf`: 返回枚举值,表示文本的情感倾向(积极、消极或中性)。

### 数字类型
对于数字类型的处理,LangChain4j同样提供了强大的支持:


```java
public interface NumberExtractor {
    
    // text=我赚了100块
    @UserMessage("Extract a number from {{it}}")
    int extractInt(String text);

    // text=我赚了100块
    @UserMessage("Extract a long number from {{it}}")
    long extractLong(String text);

    // text=我赚了100块
    @UserMessage("Extract a big integer from {{it}}")
    BigInteger extractBigInteger(String text);

    // text=我赚了100块
    @UserMessage("Extract a float number from {{it}}")
    float extractFloat(String text);

    // text=我赚了100块
    @UserMessage("Extract a double number from {{it}}")
    double extractDouble(String text);

    // text=我赚了100块
    @UserMessage("Extract a big decimal from {{it}}")
    BigDecimal extractBigDecimal(String text);
}

```

这个`NumberExtractor`接口展示了如何从文本中提取各种数值类型,包括整数、长整数、大整数、浮点数、双精度浮点数和大小数。

### 自定义POJO

LangChain4j还支持将LLM输出解析为自定义的POJO对象: 

```java
@AiService
public interface PersonExtractor {

    @UserMessage("Extract information about a person from {{it}}")
    Person extractPerson(String text);

    @Data
    class Person {
        @Description("name of a person") // 增加字段描述，让大模型更理解字段含义
        private String name;
        private LocalDate birthDate;
    }
}

```

在这个例子中,我们定义了一个`Person`类作为自定义POJO,包含name 和birthDate字段。`extractPerson`方法将从给定文本中提取人物信息并返回一个`Person`对象。

通过掌握这些核心组件,我们就能更好地利用LangChain4j来处理大语言模型的结构化输出,为我们的AI应用开发带来更多可能性。

