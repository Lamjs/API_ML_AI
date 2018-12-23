# API_ML_AI
## product requirement


| Target release | 30/11/2018 | 
| ------ | ------ |
| Epic |中文解析程序 |
| Document status | `进行中;` |
| Document owner | Lamjs |
| Designer | Lamjs |
| Developer | Lamjs |
| QA | Lamjs |


## 产品目标
- 解决用户学习中文时遇到不懂词性，因此不能正确理解语句意思时的问题，给予正确提示或答案，即标记每个词语的语义并赋予解释。



## 产品宣言
- 到目前为止，总共有67个国家和地区将汉语教学纳入了国民教育体系，且据目前部分国家的调查数据显示，中文是外国家长最想让他们的孩子学习的语言，他们认为中文是“未来最有用的”语言，且大多数国家开设中文课程，对外汉语老师供不应求，市场缺口巨大。面对汉语的普及，便用一款基于“语义分割”的学习软件帮助学习者更好的了解汉语，辅助学习。
## 产品核心价值
- （（Minimum Viable Product，最小可用产品））通过词性的解析对句子进行更好的理解，也可以单独输入成语或词语查看解释，针对外国中文爱好者提供解析英译的功能。

## 用户痛点
- 外国中文爱好者在学习中文的过程中一下子查新闻字典查看字义，一下子查成语词典学成语，且因为不熟悉拼音的他们查起来相当的费劲，又如牙牙学语的幼儿，对拼音不熟悉，无法使用字词典，因此失去了更加深入汉语文化的机会，所以将新华字典、成语字典结合，提供语音输入方式，并进行句子的拆分解析，省略繁琐的查阅步骤。
## Assumptions
- 用户使用此主要功能时，主要是在遇到不懂的复杂语句且拥有手机或其它的电子产品（ipad，电脑等）的情境下。用户通过语音输入，拼音输入或手写输入等方式向软件传达他们的请求，即会收到他们遇到的语句的句式结构,和词性解释。
- 连解析都看不懂的困境

## requirements


| # | Title |  user story | importance | notes |
| ------ | ------ | ------ | ------ | ------ |
| 1 | semantic segmentation_A |中文爱好者在尝试阅读中文文章时遇到了感到甚是费解的问题，他不明白“过几天天天天气不好”中的“天”是什么意思，为什么要有这么多个“天”凑在一起？对中文语法不是很熟的他需要一个 人/App 来告诉他这里的“天”都是什么意思,并且他对拼音及偏旁部首的造诣不高，很难独立完成查字典的工作，如果有一个能够语音输入的App告诉他句子的词性将会是很棒的体验。| important | App带扫描文字功能也是不错 |
| 2 | semantic segmentation_B |老外对中文成语并不熟练，他想知道一个成语在句中是作为名词还是形容词，但是连字典都不会翻的他需要有人/App来告诉他成语的意思，他并不介意是语音输入或是手写输入，如果能给予词性及句子的解析那是正好不过的了。| important | 对成语的语义分割及每个字都具有解释 |




## User_process
![process](https://github.com/Lamjs/API_ML_AI/blob/master/image/Process.png?raw=true)
(https://github.com/Lamjs/API_ML_AI/blob/master/image/Process.png?raw=true)
## Question
- 以上文件完成后能解决关于中文学习者对复杂语句难以分析的问题，缓解中文学习者学习的阻力，帮助他们更好的对中文有更深入的理解。
- 帮助非本土中文爱好者连解析都看不懂的问题，毕竟他们可以查看英文解析

## 人工智能概率性（视扫描场景为标亮，并有完整文字）
 |场景| 文字类型 | 可行概率性 |
 |------ | ------ | ------ |
 | 正常在电子产品中扫描文字| 简体字| >99%|
 |翻阅古籍或在电子产品中扫描文字| 繁体字 |>95%|
 | 在书及图片上扫描文字| 英文文字 | >90% |
 |图片扫描| 艺术字 | >25% |
 |书本扫描| 草书 | >25% |
 |进行词性分析| 简体字 | >99% |
 ## 需求列表与人工智能API
 |#| 功能|用户案例 |技术领域 |
 |------ | ------ | ------ | ------ |
 |1.| 文字识别|遇到不熟悉的字不懂拼音，难以输入|百度OCR文字识别API|
 |2.| 词法分析 |对句子中有多次重复的字而导致的无法理解进行梳理| 百度词法分析|
 |3.| 查询字义 |想了解文字意思 | 新闻字典API |
 |4.|翻译 | 针对不懂中文想学习中文的外国中文爱好者，帮助用英文解析了解中文意思 |有道翻译API |
## 产品信息设计
![cms](https://github.com/Lamjs/API_ML_AI/blob/master/image/Pro_info.png?raw=true)
(https://github.com/Lamjs/API_ML_AI/blob/master/image/Pro_info.png?raw=true)
## API使用水平
```
  pip install baidu-aip
  python setup.py install
  from aip import AipNlp
       APP_ID = 'Your_ID'
       API_KEY = 'Your API_KEY'
       SECRET_KEY = 'Your SECRET_KEY'
       client = AipNlp(APP_ID, API_KEY, SECRET_KEY)
       text = "小偷偷偷偷东西"

       """ 调用词法分析 """
       ss=client.lexerCustom(text);
       print(ss)
       text = "小偷偷偷偷东西"

       """ 调用依存句法分析 """
       a=client.depParser(text);

       """ 如果有可选参数 """
       options = {}
       options["mode"] = 1

       """ 带参数调用依存句法分析 """
       client.depParser(text, options)
       print(a)

```
![seg](https://github.com/Lamjs/API_ML_AI/blob/master/image/segmatic.png?raw=true)
(https://github.com/Lamjs/API_ML_AI/blob/master/image/segmatic.png?raw=true)
## character recognition
`pip install baidu-aip`
```
from aip import AipOcr
import re
APP_ID='ID'
API_KEY ='KEY'
SECRECT_KEY='S_KEY'
client=AipOcr(APP_ID,API_KEY,SECRECT_KEY)
i=open(r'117663532320130525131400277.jpg','rb')
img=i.read()
message=client.basicGeneral(img)
print(message)
```
![exam](https://github.com/Lamjs/API_ML_AI/blob/master/image/word.png?raw=true)
（https://github.com/Lamjs/API_ML_AI/blob/master/image/word.png?raw=true）

## 新华字典api
```
import json, urllib
from urllib import urlencode
def request6(appkey, m="GET"):
    url = "http://v.juhe.cn/xhzd/queryid"
    params = {
        "word" : "", #填写需要查询的汉字id
        "key" : appkey, #应用APPKEY(应用详细页查询)
        "dtype" : "", #返回数据的格式,xml或json，默认json
 
    }
    params = urlencode(params)
    if m =="GET":
        f = urllib.urlopen("%s?%s" % (url, params))
    else:
        f = urllib.urlopen(url, params)
 
    content = f.read()
    res = json.loads(content)
    if res:
        error_code = res["error_code"]
        if error_code == 0:
            #成功请求
            print res["result"]
        else:
            print "%s:%s" % (res["error_code"],res["reason"])
    else:
        print "request api error"
        
        if __name__ == '__main__':
              main()
```
## API使用比较分析
 |API类型| 分析 |
 |------ | ------ |
 |搜狗OCR API|识别速度快，准确率高，对文字大小要求严格 |
 |文通OCR API| 识别速度快，识别正确率高，并支持生成word文档 |
 |阿里云OCR API| 高准确率，高实时性，支持多种图片类型，但价格昂贵 |
 |汉王OCR API| 高准确率，支持多种图片类型，识别速度慢 |
 |百度OCR API| 准确率高，实时性良好，价格免费，对图片要求一般 |
 - 综合比较，百度OCR文字识别在价格、识别速度、图片类型、场景需求等表现良好，是目前找过API最为适用的。参考来自[此链接](https://www.jb51.net/office/601010.html)
 
## 交互及界面设计
![image](https://github.com/Lamjs/API_ML_AI/blob/master/image/process_one.png?raw=true)
![image](https://github.com/Lamjs/API_ML_AI/blob/master/image/process_two.png?raw=true)
![image](https://github.com/Lamjs/API_ML_AI/blob/master/image/process_three.png?raw=true)
(https://github.com/Lamjs/API_ML_AI/blob/master/image/process_one.png?raw=true)
(https://github.com/Lamjs/API_ML_AI/blob/master/image/process_two.png?raw=true)
(https://github.com/Lamjs/API_ML_AI/blob/master/image/process_three.png?raw=true)
## 风险及报告
`我一把把把把住了`
！[image](https://github.com/Lamjs/API_ML_AI/blob/master/image/seg.png?raw=true)
- 对于文中出现的把分析为“数词”，即有可能对句子结构复杂，类似于句中出现多个重复字体，或是有方言成分的句子难以辩解。
- 新闻字典API对申请者并不友好，需要实名并要给予两个月认证时间，在API竞争市场中不会太好。

## Not doing
- 后续解析会推出翻译语言不只又英语的各种语言。
