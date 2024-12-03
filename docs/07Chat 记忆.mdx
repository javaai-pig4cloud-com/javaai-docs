---
title: Chat 记忆缓存
---

<img src='https://minio.pigx.top/oss/202410/1728298660.png' alt='1728298660'/>

记忆缓存是聊天系统中的一个重要组件，用于存储和管理对话的上下文信息。它的主要作用是让AI助手能够"记住"之前的对话内容，从而提供连贯和个性化的回复。

## 1. 简介

ChatMemory是一个用于管理聊天上下文的组件,它可以解决以下问题:

- 防止上下文超出大模型的token限制
- 隔离不同用户的上下文信息
- 简化ChatMessage的管理


<img src='https://minio.pigx.top/oss/202410/1728219300.png' alt='1728219300'/>


## 2. 核心功能

- 容器管理: 管理ChatMessage的生命周期
- 淘汰机制: 防止存储过多消息
- 持久化: 避免聊天上下文丢失

## 3. ChatMemory实现类

LangChain4j提供了两种主要的ChatMemory实现类,每种都有其特定的用途和优势:

### 3.1 MessageWindowChatMemory（简单实现）

这是一个基于消息数量的简单实现。它采用滑动窗口的方式,保留最新的N条消息,并淘汰旧消息。

**特点:**
- 易于理解和实现
- 基于消息数量进行管理
- 适用于不需要精确token控制的场景

**使用示例:**
```java
ChatMemory chatMemory = MessageWindowChatMemory.withMaxMessages(10);
```

### 3.2 TokenWindowChatMemory（复杂实现）

这是一个更复杂的实现,它同样采用滑动窗口的方式,但侧重于保留最新的tokens,而不是消息数量。

**特点:**
- 更精确的token控制
- 需要结合Tokenizer计算ChatMessage的token数量
- 适用于需要严格控制token使用的场景

**使用示例:**
```java
Tokenizer tokenizer = new OpenAiTokenizer(GPT_3_5_TURBO);
ChatMemory chatMemory = TokenWindowChatMemory.withMaxTokens(1000, tokenizer);
```

**注意:** 使用TokenWindowChatMemory需要提供一个Tokenizer实例,用于计算消息的token数量。不同的语言模型可能需要不同的Tokenizer。

## 4. 实现方式


### 4.0 Ai Services 定义

```java

public interface ChatAssistant {

    /**
     * 聊天
     *
     * @param message 消息
     * @return {@link String }
     */
    String chat(String message);


    /**
     * 聊天
     *
     * @param userId  用户 ID  (根据ID隔离记忆)
     * @param message 消息
     * @return {@link String }
     */
    String chat(@MemoryId Long userId, @UserMessage String message);
}
```

### 4.1 共享ChatMemory

适用于单用户场景。

```java
ChatMemory chatMemory = MessageWindowChatMemory.withMaxMessages(10);
ChatAssistant assistant = AiServices.builder(ChatAssistant.class)
        .chatLanguageModel(chatLanguageModel)
        .chatMemory(chatMemory)
        .build();

String answer1 = assistant.chat("你好！我的名字是冷冷.");
String answer2 = assistant.chat("我的名字是什么？");
```

### 4.2 独享ChatMemory

适用于多用户场景。

```java
ChatAssistant assistant = AiServices.builder(ChatAssistant.class)
        .chatLanguageModel(chatLanguageModel)
        // 注意每个memoryId对应创建一个ChatMemory
        .chatMemoryProvider(memoryId -> MessageWindowChatMemory.withMaxMessages(10))
        .build();


assistant.chat(1L, "你好！我的名字是冷冷1.");
assistant.chat(2L, "你好！我的名字是冷冷2.");

String chat = assistant.chat(1L, "我的名字是什么");
System.out.println(chat);
chat = assistant.chat(2L, "我的名字是什么");
System.out.println(chat);
```

## 5. 自定义持久化

如需自定义持久化方式,可以实现ChatMemoryStore接口:

```java
public class PersistentChatMemoryStore implements ChatMemoryStore {
    private final DB db = DBMaker.fileDB("./chat-memory.db").transactionEnable().make();
    private final Map<Integer, String> map = db.hashMap("messages", INTEGER, STRING).createOrOpen();

    @Override
    public List<ChatMessage> getMessages(Object memoryId) {
        String json = map.get((int) memoryId);
        return messagesFromJson(json);
    }

    @Override
    public void updateMessages(Object memoryId, List<ChatMessage> messages) {
        String json = messagesToJson(messages);
        map.put((int) memoryId, json);
        db.commit();
    }

    @Override
    public void deleteMessages(Object memoryId) {
        map.remove((int) memoryId);
        db.commit();
    }
}
```

## 6. 注意事项

- SystemMessage会被特殊处理,始终保留且只允许一个
- 工具消息(如函数调用)需要成对处理
- 默认实现是基于内存的,如需持久化需自行实现

## 7. 最佳实践

1. 根据实际需求选择共享或独享ChatMemory
2. 合理选择ChatMemory实现类:
   - 对于简单场景,使用MessageWindowChatMemory
   - 对于需要精确控制token的场景,使用TokenWindowChatMemory
3. 合理设置消息窗口大小或token限制,平衡上下文信息和性能
4. 针对多用户场景,使用独享ChatMemory并提供唯一的memoryId
5. 如有持久化需求,自定义实现ChatMemoryStore接口
6. 注意处理特殊消息类型,如SystemMessage和工具消息

通过合理使用ChatMemory,可以有效管理聊天上下文,提升大模型应用的用户体验和性能。选择合适的ChatMemory实现类和配置可以帮助您在保留必要上下文信息和控制资源使用之间取得平衡。



