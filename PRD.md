## product requirement


| Target release | 24/11/2018 | 
| ------ | ------ |
| Epic |中文解析程序 |
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
- 连解析都看不懂的困境

## requirements


| # | Title |  user story | importance | notes |
| ------ | ------ | ------ | ------ | ------ |
| 1 | semantic segmentation_A |中文爱好者在尝试阅读中文文章时遇到了感到甚是费解的问题，他不明白“过几天天天天气不好”中的“天”是什么意思，为什么要有这么多个“天”凑在一起？对中文语法不是很熟的他需要一个 人/App 来告诉他这里的“天”都是什么意思,并且他对拼音及偏旁部首的造诣不高，很难独立完成查字典的工作，如果有一个能够语音输入的App告诉他句子的词性将会是很棒的体验。| important | App带扫描文字功能也是不错 |
| 2 | semantic segmentation_B |老外对中文成语并不熟练，他想知道一个成语在句中是作为名词还是形容词，但是连字典都不会翻的他需要有人/App来告诉他成语的意思，他并不介意是语音输入或是手写输入，如果能给予词性及句子的解析那是正好不过的了。| important | 对成语的语义分割及每个字都具有解释 |


## User interaction and design
![cms](https://github.com/Lamjs/API_ML_AI/blob/master/image/brain.png?raw=true)

## User_process
![process](https://github.com/Lamjs/API_ML_AI/blob/master/image/Process.png?raw=true)

## Question
- 以上文件完成后能解决关于中文学习者对复杂语句难以分析的问题，缓解中文学习者学习的阻力，帮助他们更好的对中文有更深入的理解。
- 帮助非本土中文爱好者连解析都看不懂的问题，毕竟他们可以查看英文解析

## semantic segmentation_code
```
  pip install baidu-aip
  python setup.py install
  from aip import AipNlp
       APP_ID = 'Your_ID'
       API_KEY = 'Your API_KEY'
       SECRET_KEY = 'Your SECRET_KEY'
       client = AipNlp(APP_ID, API_KEY, SECRET_KEY)
       text = "新媒体研究中心打造以人为本的交互设计及数据计量，求网络和真实世界的可持续发展。"

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
## character recognition
```
     from aip import AipOcr

    """ 你的 APPID AK SK """
        APP_ID = '你的 App ID'
        API_KEY = '你的 Api Key'
        SECRET_KEY = '你的 Secret Key'

       client = AipOcr(APP_ID, API_KEY, SECRET_KEY)
       
       """ 读取图片 """
def get_file_content(filePath):
    with open(filePath, 'rb') as fp:
        return fp.read()

image = get_file_content('example.jpg')

""" 调用通用文字识别, 图片参数为本地图片 """
client.basicGeneral(image);

""" 如果有可选参数 """
options = {}
options["language_type"] = "CHN_ENG"
options["detect_direction"] = "true"
options["detect_language"] = "true"
options["probability"] = "true"

""" 带参数调用通用文字识别, 图片参数为本地图片 """
client.basicGeneral(image, options)

url = "http//www.x.com/sample.jpg"

""" 调用通用文字识别, 图片参数为远程url图片 """
client.basicGeneralUrl(url);

""" 如果有可选参数 """
options = {}
options["language_type"] = "CHN_ENG"
options["detect_direction"] = "true"
options["detect_language"] = "true"
options["probability"] = "true"

""" 带参数调用通用文字识别, 图片参数为远程url图片 """
client.basicGeneralUrl(url, options)
```
（http://ai.baidu.com/docs#/OCR-Python-SDK/07883957）

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

## Not doing
- 文字扫描
- 语音输入
- 语音播报
