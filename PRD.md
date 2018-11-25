## product requirement


| Target release | 24/11/2018 | 
| ------ | ------ |
| Epic | 解决学习中文时看到“小偷偷偷偷东西”不懂里面词性的问题 |
| Document status | `进行中;` |
| Document owner | Lamjs |
| Designer | Lamjs |
| Developer | Lamjs |
| QA | Lamjs |


## Goals
- 解决用户学习中文时遇到不懂词性，因此不能正确理解语句意思时的问题，给予正确提示或答案，即标记每个词语的语义并赋予解释。



## Background and strategic fit
- 汉语在国际上逐渐普及，很多学习者不懂中文词性而导致对句子的理解不透，所以想用一款基于“语义分割”的学习软件帮助学习者更好的了解汉语。


## Assumptions
- 用户使用此主要功能时，主要是在遇到不懂的复杂语句且拥有手机或其它的电子产品（ipad，电脑等）的情境下。用户通过语音输入，拼音输入或手写输入等方式向软件传达他们的请求，即会收到他们遇到的语句的句式结构,和词性解释。


## requirements


| # | Title |  user story | importance | notes |
| ------ | ------ | ------ | ------ | ------ |
| 1 | semantic segmentation_A |中文爱好者在尝试阅读中文文章时遇到了感到甚是费解的问题，他不明白“过几天天天天气不好”中的“天”是什么意思，为什么要有这么多个“天”凑在一起？对中文语法不是很熟的他需要一个 人/App 来告诉他这里的“天”都是什么意思,并且他对拼音及偏旁部首的造诣不高，很难独立完成查字典的工作，如果有一个能够语音输入的App告诉他句子的词性将会是很棒的体验。| 迫切需要一款能够语义分析的app来帮助他们更好的阅读理解 | App带扫描文字功能也是不错 |
| 2 | semantic segmentation_B |老外对中文成语并不熟练，他想知道一个成语在句中是作为名词还是形容词，但是连字典都不会翻的他需要有人/App来告诉他成语的意思，他并不介意是语音输入或是手写输入，如果能给予词性及句子的解析那是正好不过的了。| 语义分割对学习帮助巨大 | 对成语的语义分割及每个字都具有解释 |


## User interaction and design

mermaid
graph LR
    start[开始] --> input[输入A,B,C]
    input --> conditionA{A是否大于B}
    conditionA -- YES --> conditionC{A是否大于C}
    conditionA -- NO --> conditionB{B是否大于C}
    conditionC -- YES --> printA[输出A]
    conditionC -- NO --> printC[输出C]
    conditionB -- YES --> printB[输出B]
    conditionB -- NO --> printC[输出C]
    printA --> stop[结束]
    printC --> stop
    printB --> stop


## Question
- 以上文件完成后能解决关于中文学习者对复杂语句难以分析的问题，缓解中文学习者学习的阻力，帮助他们更好的对中文有更深入的理解。

## Not doing
- 文字扫描
- 语音输入
