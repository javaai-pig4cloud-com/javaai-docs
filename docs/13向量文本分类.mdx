---
title: 文本向量化分类
---

> 智慧HR: 基于LangChain4j文本向量的面试者性格特征匹配

性格特征匹配是HR领域的一项重要任务，它通过分析面试者的语言表达、行为模式等信息，将其与预定义的性格标签进行匹配。这有助于HR专业人士更好地评估候选人是否适合特定职位或团队文化。

## LangChain4j中的文本分类支持

LangChain4j框架通过`TextClassifier`接口，结合向量模型，为我们提供了实现性格特征匹配的强大工具。

### 基于向量模型的分类器实现

`EmbeddingModelTextClassifier`通过向量模型对文本进行向量化，并利用余弦相似度计算文本与性格标签之间的匹配度。


### 配置 EmbeddingModel

```java
@Bean
public EmbeddingModel embeddingModel() {
    return OpenAiEmbeddingModel.builder()
            .apiKey(System.getenv("DASHSCOPE_KEY"))
            .modelName("text-embedding-v3")
            .baseUrl("https://dashscope.aliyuncs.com/compatible-mode/v1")
            .build();
}
```

### 定义业务枚举

```java
@Getter
@AllArgsConstructor
public enum PersonalityTrait {
    /**
     * 外向型：喜欢社交，从与他人互动中获得能量
     */
    EXTROVERT,

    /**
     * 内向型：倾向于独处，需要安静时间来恢复能量
     */
    INTROVERT,

    /**
     * 分析型：擅长逻辑思考，喜欢解决复杂问题
     */
    ANALYTICAL,

    /**
     * 创意型：富有想象力，常有新颖的想法
     */
    CREATIVE,

    /**
     * 领导型：善于指导他人，乐于承担责任
     */
    LEADER,

    /**
     * 团队合作型：重视协作，善于在团队中工作
     */
    TEAM_PLAYER
}
```

### 配置向量文本分类器

```java
@Bean
public EmbeddingModelTextClassifier<PersonalityTrait> textClassifier(EmbeddingModel embeddingModel) {
    return new EmbeddingModelTextClassifier<>(embeddingModel, PersonalityTraitExamples.examples);
}
```

### 示例数据

```java
public class PersonalityTraitExamples {
    public static final Map<PersonalityTrait, List<String>> examples = Map.of(
            PersonalityTrait.EXTROVERT, List.of(
                    "我喜欢结识新朋友",
                    "团体活动让我充满活力",
                    "我经常是聚会的焦点",
                    "我喜欢在热闹的社交环境中工作"
            ),
            PersonalityTrait.INTROVERT, List.of(
                    "我更喜欢独自工作",
                    "我需要安静的时间来充电",
                    "大型社交聚会让我感到压抑",
                    "我喜欢深入的一对一谈话"
            ),
            PersonalityTrait.ANALYTICAL, List.of(
                    "我喜欢解决复杂的问题",
                    "数据驱动的决策至关重要",
                    "我总是寻找信息中的模式和联系",
                    "我倾向于在采取行动之前彻底分析情况"
            ),
            PersonalityTrait.CREATIVE, List.of(
                    "我常常跳出框架思考",
                    "我总是想出新的点子",
                    "我喜欢寻找创新的解决方案",
                    "我受到周围艺术和美的启发"
            ),
            PersonalityTrait.LEADER, List.of(
                    "我能自信地领导项目",
                    "我激励他人实现目标",
                    "我喜欢指导和培养团队成员",
                    "我不怕做出艰难的决定"
            ),
            PersonalityTrait.TEAM_PLAYER, List.of(
                    "合作是成功的关键",
                    "我重视所有团队成员的意见",
                    "我总是愿意帮助我的同事",
                    "我相信团队中多样化视角的力量"
            )
    );
}
```

### 测试

```java
@Autowired
private EmbeddingModelTextClassifier<PersonalityTrait> textClassifier;

@Test
void analyzePersonality() {
    List<PersonalityTrait> classify = textClassifier.classify("赠人玫瑰，手有余香");
    System.out.println(classify);
}
```


## 源码解析

```java
/**
 * 基于嵌入模型的文本分类器
 * 这个分类器使用嵌入模型来对文本进行分类,通过比较待分类文本的嵌入与每个标签的示例文本嵌入的相似度来实现分类。
 *
 * @param <E> 标签的枚举类型
 */
public class EmbeddingModelTextClassifier<E extends Enum<E>> implements TextClassifier<E> {

    // 用于生成文本嵌入的嵌入模型
    private final EmbeddingModel embeddingModel;
    
    // 存储每个标签对应的示例文本嵌入
    private final Map<E, List<Embedding>> exampleEmbeddingsByLabel;
    
    // 分类结果返回的最大标签数量
    private final int maxResults;
    
    // 分类时的最小相似度得分阈值
    private final double minScore;
    
    // 平均得分和最大得分的权重比例
    private final double meanToMaxScoreRatio;

    /**
     * 使用默认参数创建分类器
     * maxResults默认为1, minScore默认为0, meanToMaxScoreRatio默认为0.5
     *
     * @param embeddingModel  用于嵌入示例和待分类文本的嵌入模型
     * @param examplesByLabel 每个标签对应的示例文本集合,示例越多效果越好
     */
    public EmbeddingModelTextClassifier(EmbeddingModel embeddingModel,
                                        Map<E, ? extends Collection<String>> examplesByLabel) {
        this(embeddingModel, examplesByLabel, 1, 0, 0.5);
    }

    /**
     * 创建分类器的完整构造函数
     *
     * @param embeddingModel      用于嵌入示例和待分类文本的嵌入模型
     * @param examplesByLabel     每个标签对应的示例文本集合
     * @param maxResults          每次分类返回的最大标签数量
     * @param minScore            分类的最小相似度得分阈值,范围[0..1]
     * @param meanToMaxScoreRatio 平均得分和最大得分的权重比例,范围[0..1]
     *                            0表示仅使用平均得分,1表示仅使用最大得分,0.5表示平均和最大得分equally加权
     */
    public EmbeddingModelTextClassifier(EmbeddingModel embeddingModel,
                                        Map<E, ? extends Collection<String>> examplesByLabel,
                                        int maxResults,
                                        double minScore,
                                        double meanToMaxScoreRatio) {
        // 参数校验
        this.embeddingModel = ensureNotNull(embeddingModel, "embeddingModel");
        ensureNotNull(examplesByLabel, "examplesByLabel");

        // 预计算并存储所有示例文本的嵌入
        this.exampleEmbeddingsByLabel = new HashMap<>();
        examplesByLabel.forEach((label, examples) ->
                exampleEmbeddingsByLabel.put(label, embeddingModel.embedAll(
                    examples.stream()
                        .map(TextSegment::from)
                        .collect(toList())).content()
                )
        );

        // 设置其他参数
        this.maxResults = ensureGreaterThanZero(maxResults, "maxResults");
        this.minScore = ensureBetween(minScore, 0.0, 1.0, "minScore");
        this.meanToMaxScoreRatio = ensureBetween(meanToMaxScoreRatio, 0.0, 1.0, "meanToMaxScoreRatio");
    }

    /**
     * 对给定文本进行分类
     *
     * @param text 待分类的文本
     * @return 分类结果,即最相似的标签列表
     */
    @Override
    public List<E> classify(String text) {
        // 获取待分类文本的嵌入
        Embedding textEmbedding = embeddingModel.embed(text).content();

        List<LabelWithScore> labelsWithScores = new ArrayList<>();
        
        // 计算待分类文本与每个标签的示例文本的相似度
        exampleEmbeddingsByLabel.forEach((label, exampleEmbeddings) -> {
            double meanScore = 0;
            double maxScore = 0;
            
            // 计算与每个示例的相似度
            for (Embedding exampleEmbedding : exampleEmbeddings) {
                double cosineSimilarity = CosineSimilarity.between(textEmbedding, exampleEmbedding);
                double score = RelevanceScore.fromCosineSimilarity(cosineSimilarity);
                meanScore += score;
                maxScore = Math.max(score, maxScore);
            }
            meanScore /= exampleEmbeddings.size();

            // 计算该标签的综合得分
            labelsWithScores.add(new LabelWithScore(label, aggregatedScore(meanScore, maxScore)));
        });

        // 根据得分筛选并排序标签
        return labelsWithScores.stream()
                .filter(it -> it.score >= minScore)
                // 按得分降序排序
                .sorted(comparingDouble(labelWithScore -> 1 - labelWithScore.score))
                .limit(maxResults)
                .map(it -> it.label)
                .collect(toList());
    }

    /**
     * 计算平均得分和最大得分的加权综合得分
     */
    private double aggregatedScore(double meanScore, double maxScore) {
        return (meanToMaxScoreRatio * meanScore) + ((1 - meanToMaxScoreRatio) * maxScore);
    }

    /**
     * 内部类,用于存储标签及其对应的得分
     */
    private class LabelWithScore {
        private final E label;
        private final double score;

        private LabelWithScore(E label, double score) {
            this.label = label;
            this.score = score;
        }
    }
}
```