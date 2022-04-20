##  决策树：判断语句是native speaker还是chinese写的

### 数据来源：

共129条数据，native speaker 64条，chinese 65条，数据主要来自8篇论文的introduction部分（四篇native speaker、四篇chinese）；
训练集103条，测试集26条，为避免过拟合使用剪枝，最后在测试集准确率到0.7左右

### 特征选择：

共10个特征，谓语数量、非谓语数量、副词数量、从句个数、插入语个数、被动状态个数（主从句的被动结构）、连词个数（but、and、because等）、
句子类型判定（复合句、并列句、简单句）；
对所有特征在建模时按照浮点数处理（不影响分类效果），最后可视化决策树时可以再进行取整处理。

### 样例：

In this work we propose the Transformer, a model architecture eschewing recurrence and instead relying entirely on an attention mechanism to draw global dependencies between input and output.
主句谓语：propose
非谓语结构：schewing、relying、to traw
副词：entirely、instead
无从句、无插入语
简单句：无被动形态
连词：and、and
label：1（native speaker）

### 数据集分析：

1、从句包括非限制性定语从句、定语从句、主语从句等，从句个数越多，句子结构越复杂；
2、插入语的存在会使句子结构更复杂、逻辑关系等信息更丰富，native speaker使用插入语的次数更多；
3、native speaker更喜欢使用程度副词，例如,often、only、nearly等；
4、连词个数可以描述句子的并列成分个数，比并列句描述的信息更多，当主句中没有连词但从句中存在连词时，句子虽不是并列句，但存在并列结构，包含的信息更多；
5、native speaker使用非谓语次数也更多，非谓语包括不定时、过去分词以及动名词结构，非谓语数量的增加在一定程度上增加了句子的复杂性；
6、native speaker更喜欢写复合句，即句子由一个主句和一个或一个以上的从句构成，句子结构更复杂，其中，native speaker也偏好并列复合句；
简单句的判定作为分类依据效果一般，例如，简单句但是多非谓语结构的倾向性也许不强；
7、（并列）谓语数量可以反应句子的复杂程度，并列谓语数量越多，句子结构越复杂，相对于chinese，native speaker会倾向使用更多的（并列）谓语结构；
8、被动状态可以在一定程度上体现句子的逻辑偏好，但目前标注的数据中存在较少，作为分类依据效果一般；

### 关于可视化结果：

![avatar](https://s1.328888.xyz/2022/04/20/rmJgk.png) 

红色为chinese ，蓝色为native speaker；
非叶子结构的颜色是指两个类别的占比，颜色越深对应类别的数量占比越大；
叶子结构的颜色对应分类结果。

### 结论：

相对于chinese，native speaker的句子结构更复杂，会使用更多的从句、插入语、程度副词、连词以及非谓语结构，native speaker更倾向于写并列复合句（即是并列句又包含从句）



