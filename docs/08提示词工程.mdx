---
title: 提示词工程
---


在本文中，我们将探讨如何利用LangChain4j框架构建一个专业的法律咨询助手。这个助手将专注于回答中国法律相关问题，对其他领域的咨询则会礼貌地拒绝。我们将深入了解角色设定和提示词模板的使用，这是实现这个功能的两个关键要素。

## 角色设定：塑造AI助手的专业身份

角色设定是指导大语言模型(LLM)行为的重要手段。通过明确定义AI助手的身份和能力范围，我们可以使其更专注于特定领域的任务。在LangChain4j中，我们主要利用`SystemMessage`来实现这一点。

`SystemMessage`具有高优先级，能有效地指导模型的整体行为。例如，我们可以这样定义一个专业法律顾问的角色：

```java
@SystemMessage("你是一位专业的中国法律顾问，只回答与中国法律相关的问题。输出限制：对于其他领域的问题禁止回答，直接返回'抱歉，我只能回答中国法律相关的问题。'")
```

## 提示词模板：精确控制输入输出

LangChain4j提供了多种方式来使用提示词模板，让我们能够灵活地构造输入并控制输出。以下是几种常用的方法：

#### 1. 使用 `@UserMessage` 和 `@V` 注解：

```java
public interface AiAssistant {
    @SystemMessage("你是一位专业的中国法律顾问，只回答与中国法律相关的问题。输出限制：对于其他领域的问题禁止回答，直接返回'抱歉，我只能回答中国法律相关的问题。'")
    @UserMessage("请回答以下法律问题：{{question}}")
    String answerLegalQuestion(@V("question") String question);
}
```

#### 2. 使用 `@StructuredPrompt` 定义结构化提示：

```java
@Data
@StructuredPrompt("根据中国{{legal}}法律，解答以下问题：{{question}}")
class LegalPrompt {
    private String legal;
    private String question;
}
```

```java
public interface AiAssistant {
    @SystemMessage("你是一位专业的中国法律顾问，只回答与中国法律相关的问题。输出限制：对于其他领域的问题禁止回答，直接返回'抱歉，我只能回答中国法律相关的问题。'")
    String answerLegalQuestion(LegalPrompt prompt);
}
```

#### 3. 使用 `PromptTemplate` 渲染：

```java
// 默认 form 构造使用 it 属性作为默认占位符
PromptTemplate template = PromptTemplate.from("请解释中国法律中的'{{it}}'概念。");
Prompt prompt = template.apply("知识产权");
System.out.println(prompt.text()); // 输出: 请解释中国法律中的'知识产权'概念。

// apply 方法接受 Map 作为参数
PromptTemplate template2 = PromptTemplate.from("请解释中国法律中的'{{legal}}'概念。");
Prompt prompt2 = template2.apply(Map.of("legal", "知识产权"));
System.out.println(prompt2.text());
```

## 实现专业法律咨询助手

现在，让我们来实现这个专业的法律咨询助手。

#### 1. 定义 `LegalAdvisor` 接口：

```java
@AiService
public interface LegalAssistant {
    @SystemMessage("你是一位专业的中国法律顾问，只回答与中国法律相关的问题。对于其他领域的问题，请回复'抱歉，我只能回答中国法律相关的问题。'")
    @UserMessage("请回答以下法律问题：{{question}}")
    String answerLegalQuestion(@V("question") String question);
}
```

#### 2. 创建一个控制器来处理法律咨询请求：

```java
/**
 * 法律咨询控制器
 *
 * @author lengleng
 */
@RestController
public class LegalAdvisorController {

    @Autowired
    private LegalAssistant legalAssistant;

    @GetMapping("/legal")
    public String getLegalAdvice(@RequestParam("question") String question) {
        return legalAssistant.answerLegalQuestion(question);
    }
}
```

## 测试与效果

使用这个法律咨询助手，我们可以得到以下效果：

1. 法律相关问题：
   输入: "什么是著作权？"
   输出: "著作权是指作者对其创作的文学、艺术和科学作品所享有的专有权利。在中国，著作权自作品创作完成之日起自动产生，无需注册。它包括发表权、署名权、修改权、保护作品完整权等人身权利，以及复制权、发行权、出租权、展览权、表演权、放映权、广播权、信息网络传播权、摄制权、改编权、翻译权和汇编权等财产权利。著作权的保护期通常是作者终生加死后50年。"

2. 非法律问题：
   输入: "请介绍一下人工智能技术"
   输出: "抱歉，我只能回答中国法律相关的问题。"

## 总结

通过LangChain4j框架，我们成功实现了一个专注于中国法律咨询的AI助手。关键点在于：

1. 使用`SystemMessage`明确定义助手的角色和能力范围，将其限定在法律咨询领域。
2. 利用提示词模板(`@UserMessage`, `@V`)精确控制输入和期望的输出格式，确保问题被正确理解和回答。
3. 在接口中组合使用这些注解，轻松实现复杂的AI交互逻辑，使助手能够识别并回应法律相关问题。

这个例子展示了LangChain4j在构建专业化AI应用方面的强大功能和灵活性。通过合理设置角色和精心设计提示词，我们可以创建出专注于特定领域（如法律咨询）的AI助手，为用户提供准确、相关的信息和建议。这种方法不仅提高了AI助手的实用性，还确保了其在专业领域内的可靠性和专业性。