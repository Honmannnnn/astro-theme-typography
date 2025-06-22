---
title: Python爬虫
pubDate: 2022-08-30
categories: ['Python']
description: '这篇笔记是关于自动获取网页数据信息的爬虫程序，是网站搜索引擎的重要组成部分。一般人能访问到的网页，爬虫也都能抓取。所谓的爬虫抓取，就是模拟人类访问目标网站。但和普通人访问方式不同，爬虫是可以按照一定的规则，自动的采集数据新'
slug: Python Web Crawler
---

# Python爬虫



## 什么是爬虫

**通过编写程序，模拟浏览器上网，然后让其去互联网上抓取数据的过程。**

> 是一种自动获取网页数据信息的爬虫程序，是网站搜索引擎的重要组成部分。一般人能访问到的网页，爬虫也都能抓取。所谓的爬虫抓取，就是模拟人类访问目标网站。但和普通人访问方式不同，爬虫是可以按照一定的规则，自动的采集数据新。

## 爬虫的价值

**在互联网中，数据是无价之宝，一切皆为数据，谁拥有大量有用 的数据，谁就拥有了决策的主动权。**网络爬虫的应用领域很多，eg：爬取需要的数据进行统计、出行类软件可以利用爬虫抢票、整理聚合手机平台信息进行比较，数据分析、爬取个人信用信息。企业或政府利用爬取的数据，采用数据挖掘的相关方法，发掘用户讨论的内容、实行事件监测、舆情引导等。

## 爬虫的原理

**爬虫在使用场景中的分类分为以下4种。**

1. 通用网络爬虫

   > 又称全网爬虫，爬取对象由一批种子URL扩充到整个Web，主要由搜索引擎或大型Web服务提供使商用。

   抓取系统重要组成部分，抓取的是一整张页面的数据。

2. 聚焦网络爬虫

   > 又称主题网络爬虫，其最大的特点是只选择性地爬取与预设的主题相关的页面。

   是建立在通用网络爬虫的基础之上的，抓取的是页面中特定的局部内容。

3. 增量式网络爬虫

   > 只对已经下载玩野采取增量式更新，或只怕去新产生的及已经发生变化的网页，这种机制能够在某种程度上保证爬取的页面尽可能的新。

   检测网站中有数据更新的情况，只会抓取网站中最新更新出来的数据。

4. 深层网络爬虫

   > 指大部分内容无法通过静态链接获取，隐藏在表单后的，需要用户提交关键词后才能获得Web页面，如一些登录才可见的网页。

## 反爬机制

门户网站，可以通过制定相应的策略或者技术手段，防止爬虫程序进行网站数据的被爬取。

## 爬取策略

爬虫程序可以通过制定相关的策略或者技术手段，破解门户网站中具备的反爬机制，从而获取数据。

## robots.txt协议

该协议不是一份规范，只是一个约定俗成的协议。爬虫应当遵守这份协议，否则很可能会被万丈所有者封禁IP，甚至网站所有者会采取进一步法律行动。

> 著名的360的爬虫之争为案例

## http协议  

就是服务器和客户端进行数据交互的一种形式。

常用的请求偷头信息：

* User-Agent：请求载体身份标识。
* Connection：请求完毕后，是断开连接还是保持连接。

常用响应头信息：

* Content-Type：服务器响应回客户端的数据类型。

https协议：

* 安全的超文本传输协议

加密方式：

* 对称秘钥加密
* 非对称秘钥加密
* 证书秘钥加密



# requests模块

## request模块是什么？

python中原生的一款基于网络请求的模块

> 在python内置模块的基础上进行了高度的封装，从而使得python进行网络请求时，变得人性化，使用Requests可以轻而易举的完成浏览器可有的任何操作。

作用：模拟浏览器向服务器发请求。

## requests的安装

```bash
pip install requests
```

## http请求类型

有4种请求类型：

1. PUT
2. DELETE
3. HEAD
4. OPTIONS

```python
requests.get(‘https://github.com/timeline.json’)                                # GET请求
requests.post(“http://httpbin.org/post”)                                        # POST请求
requests.put(“http://httpbin.org/put”，data = {'key':'value'})                  # PUT请求
requests.delete(“http://httpbin.org/delete”)                                    # DELETE请求
requests.head(“http://httpbin.org/get”)                                         # HEAD请求
requests.options(“http://httpbin.org/get” )                                     # OPTIONS请求
```

## 使用流程/编码流程

1. 指定URL
2. 基于requests模块**发送请求**
3. **获取响应**对象中的**数据**值
4. 持久化存储



# 第一个简单的爬虫程序

使用request模块实现一个简单的网页采集。

## 步骤

### 指定url

如下的问号其实可以保留也可以不保留。

```python
#指定url
url = 'https://www.sogou.com/web?'
```



### User-Agent伪装

这一步需要用浏览器在开发者工具中查看自己本机的User-Agent。

```python
#UA伪装
headers = {
    'User-Agent': 'Mozilla/x.x (Macintosh; Intel Mac OS X xx_xx_x) AppleWebKit/xxx.xx (KHTML, like Gecko) Chrome/xxx.x.x.x Safari/xxx.xx'
}
```



### 响应发起请求

get请求返回的是一个response响应对象。

```python
#获取请求响应
response = requests.get(url = url,params = param,headers = headers) #get返回一个响应对象
```



### 获取响应数据

获取字符串形式的响应数据，也就是获取text的格式的响应数据。

```python
page_text = response.text #获取字符串形式的响应数据
```



### 持久化储存

这一步就是最后的操作了，把采集到的网页页面元素保存下来。

```python
with open(fileName,'w',encoding = 'utf-8') as fp:
    fp.write(page_text)
```

## 完整代码

```python
import requests

#指定url
url = 'https://www.sogou.com/web?'
#UA伪装
headers = {
    'User-Agent': 'Mozilla/x.x (Macintosh; Intel Mac OS X xx_xx_x) AppleWebKit/xxx.xx (KHTML, like Gecko) Chrome/xxx.x.x.x Safari/xxx.xx'
}

kw = input("请输入一个关键词: ")
param = {
    'query':kw
}
fileName = kw+'.html'
#获取请求响应
response = requests.get(url = url,params = param,headers = headers) #get放回一个响应对象
page_text = response.text #获取字符串形式的响应数据
with open(fileName,'w',encoding = 'utf-8') as fp:
    fp.write(page_text)

print(fileName,'save successfully')

```



# 某度翻译破解

**在pycharm中实现直接输入要翻译的英语单词，终获得翻译结果并且保存下来。**



## 指定url

利用浏览器的开发工具进行数据抓包，在XHP页面获取Ajax实际请求地址。

切换到Headers找到请求，可以看到请求的url、请求方式和返回的数据类型都有了。

```python
# 指定url
url = 'https://fanyi.baidu.com/sug'
```



## UA伪装

**让爬虫对应的请求载体身份标识伪装成某一款浏览器。**
方法：将对应的User-Agent封装到一个字典中。

```python
# UA伪装
headers = {
    'User-Agent': 'Mozilla/x.x (Macintosh; Intel Mac OS X xx_xx_x) AppleWebKit/xxx.xx (KHTML, like Gecko) Chrome/xxx.x.x.x Safari/xxx.xx'
}
```



## POST请求参数处理

在XHP页面获取Ajax实际相关参数。

```python
# post请求参数处理（同get请求一致）
data = {
    'kw': words
}
```



## 请求发送

基于requests发送请求，通过前面抓包得到的信息我们得到了，它的请求方式为post请求，这里我们使用requests模块中post()方法来发送请求

```python
# 请求发送
responce = requests.post(url=url, data=data, headers=headers)
```



## 获取响应数据

```python
# 获取响应数据：json()方法放回的是obj（确认了响应数据是json类型才可以用json()方法）
result = responce.json()  # 返回一个obj
```



## 进行持久化存储

默认使用的编码是ASCII（不包含中文），而中文是Unicode编码。

```python
# 进行持久化存储
fp = open(fileName, 'w', encoding='UTF-8')
json.dump(result, fp=fp, ensure_ascii=False)  # json()返回的obj中有中文 所以不能用ASCII解码
```



## 完整代码

```python
import requests
import json

# 指定url
url = 'https://fanyi.baidu.com/sug'

# UA伪装
headers = {
    'User-Agent': 'Mozilla/x.x (Macintosh; Intel Mac OS X xx_xx_x) AppleWebKit/xxx.xx (KHTML, like Gecko) Chrome/xxx.x.x.x Safari/xxx.xx'
}

# 输入翻译的词
words = input('请输入要翻译的英语单词: ')
# post请求参数处理（同get请求一致）
data = {
    'kw': words
}
# 请求发送
responce = requests.post(url=url, data=data, headers=headers)

fileName = words + '.json'

# 获取响应数据：json()方法放回的是obj（确认了响应数据是json类型才可以用json()方法）
result = responce.json()  # 返回一个obj
print('翻译结果如下:')
print(result)  # 打印返回的obj结果

# 进行持久化存储
fp = open(fileName, 'w', encoding='UTF-8')
json.dump(result, fp=fp, ensure_ascii=False)  # json()返回的obj中有中文 所以不能用ASCII解码
print('save over！')

```



# 正则表达式模块

**Python通过自带的re模块来支持正则表达式**

> 1. 先将正则表达式的String编译为“Pattern”实例
> 2. 使用Pattern实例处理结文本并且获得匹配结果（一个Match实例）
> 3. 使用Match实例获得信息



## re模块常用的方法

| 方法名   | 说明                                                         |
| :------- | :----------------------------------------------------------- |
| compile  | 将正则表达式String转化为Pattern匹配对象。                    |
| match    | 将输入的String从头开始对输入的正则表达式进行匹配，如果遇到无法匹配的字符或到达String的末尾，则立即放回None，否则获取匹配结果。 |
| search   | 将输入的整个String进行扫描，对输入的正则表达式进行匹配，并获取匹配结果，如果没有匹配结果，则返回None。 |
| split    | 以能够匹配的String作为分隔符，将String分割后返回一个列表。   |
| findall  | 搜索整个String，返回一个包含全部能匹配子串的列表。           |
| finditer | 与findall方法的作用类似，以迭代器的形式返回结果。            |
| sub      | 使用指定内容替换字符串中匹配的每一个子串内容。               |

### compile方法

**将正则表达式的字符串转化为Pattern匹配对象**

```python
re.compile(pattern,flags=0)
```

| 参数    | 说明                                                         |
| ------- | ------------------------------------------------------------ |
| Pattern | 接收str，表示需要转换的正则表达式的字符串。无默认值。        |
| flags   | 接收str，表示匹配的模式，取值为运算符"\|"时表示同时生效，如re.I\|re.M。默认为0。 |



### search方法

**该方法将输入的整个字符串进行扫描，并对输入的正则表达式进行匹配，若无匹配的字符，则立即返回None，否则获取匹配结果。**

```python
re.search(pattern,string,flags=0)
```

| 参数    | 说明                                                      |
| ------- | --------------------------------------------------------- |
| Pattern | 接收Pattern实例，表示转换后的正则表达式。无默认值。       |
| string  | 接收str，表示输入的需要匹配的字符串。无默认值。           |
| flags   | 接收str，表示匹配的模式，取值为运算符"\|"时表示同时生效。 |

### finall方法

**该方法搜索整个string，并放回一个包含所有能匹配的子串的列表**

```python
re.finall(pattern,string,flags=0)
```

| 参数    | 说明                                                         |
| ------- | ------------------------------------------------------------ |
| Pattern | 接收Pattern实例，表示转换后的正则表达式。无默认值。          |
| string  | 接收str，表示输入的需要匹配的字符串。无默认值。              |
| flags   | 接收str，表示匹配的模式，取值为运算符"\|"时表示同时生效，意思为“or”。 |

**使用finall方法找出字符串中的所有数字**

若 str = a1b2c3d4e5f6g7 找出其中的所有数字：

```python
import re

pat = re.compile(r'\d+')
str = 'a1b2c3d4e5f6g7'	#设定：str = a1b2c3d4e5f6g7
result = re.findall(pat, str)
print(result)   #输出：['1', '2', '3', '4', '5', '6', '7']
```



## 获取网页中的标题内容

```python
import re
import requests

url = 'http://www.tipdm.com/tipdm/index.html'

header = {
    'User-Agent': 'Mozilla/5.0 (Macintosh; Intel xxx OS X xx_xx_x) AppleWebKit/xxx.xx (KHTML, like Gecko) Chrome/xxx.x.x.x xxxxx/xxx.xx',
    'Cookie': '_site_id_cookie=xx; _site_id_cookie=xx.x; JSESSIONID=abcdefg123456abcd1234; clientlanguage=zh_CN'
}
requests_get = requests.get(url, header)
requests_get.encoding = 'utf-8'
html_text = requests_get.text

# <title>泰迪科技-专注于大数据技术研发及知识传播</title>
pattern = r'(?<=<title>).*?(?=</title>)'
result_com = re.compile(pattern)
result_search = re.search(result_com, html_text)
# <re.Match object; span=(178, 198), match='泰迪科技-专注于大数据技术研发及知识传播'>
print(result_search)
# 泰迪科技-专注于大数据技术研发及知识传播
print(result_search.group())
```

**一步到位**

```python
import re
import requests

url = 'http://www.tipdm.com/tipdm/index.html'
header = {
    'User-Agent': 'Mozilla/5.0 (Macintosh; Intel xxx OS X xx_xx_x) AppleWebKit/xxx.xx (KHTML, like Gecko) Chrome/xxx.x.x.x xxxxx/xxx.xx',
    'Cookie': '_site_id_cookie=xx; _site_id_cookie=xx.x; JSESSIONID=abcdefg123456abcd1234; clientlanguage=zh_CN'
}
requests_get = requests.get(url, header)
# requests_get.encoding = 'utf-8'
html_text = requests_get.text
# <title>泰迪科技-专注于大数据技术研发及知识传播</title>
print(re.findall(r'(?<=<title>).*?(?=</title>)', html_text))
```

>其实不推荐使用正则表达式去定位特定节点来获得其中想要的内容的。
>
>✅推荐使用：Xpath、BeautifulSoup。



# 使用Xpath解析网页

**XML路径语言（XML Path Language，Xpath）**是一门文档中查找信息的语言。



## 基础语法

使用Xpath需要从lxml库中导入etree模块，还需要使用HTML类对需要匹配的HTML对象进行初始化。HTML类对基本语法格式如下：

```python
lxml.etree.HTML(text, parser=None, *, base_url=None)
```

**HTML类对常用参数及说明如下：**

| 参数名称     | 说明                                                         |
| ------------ | ------------------------------------------------------------ |
| **text**     | 接收str 表示需要转换为HTML的字符串。无默认值                 |
| **parser**   | 接收str 表示选择的HTML解析器。无默认值                       |
| **base_url** | 接收str 表示文档的原始URL 用于查找外部实体的相对路径。默认为None |

**Xpath可以使用类似正则的表达式来匹配HTML文件中的内容，常用的表达式如下：**

| 表达式       | 说明                         |
| ------------ | ---------------------------- |
| **nodename** | 选取nodename节点的所有子节点 |
| **/**        | 从当前节点选取直接子节点     |
| **//**       | 从当前节点选取所有子孙节点   |
| **.**        | 选取当前节点                 |
| **..**       | 选取当前节点的父节点         |
| **@**        | 选取属性                     |



## 谓语

Xpath中的谓语可用来查找某个特定的节点或包含某个指定的值的节点，谓语呗嵌套在路径后面的方括号中，如下：

| 表达式                        | 说明                                                 |
| ----------------------------- | ---------------------------------------------------- |
| /html/boby/div[1]             | 选取属于body子节点的第一个的div节点                  |
| /html/boby/div[last()]        | 选取属于body子节点的最后一个div节点                  |
| /html/boby/div[last()-1]      | 选取属于body子节点的倒数第二个div节点                |
| /html/boby/div[postion()<3]   | 选取属于body子节点的前两个div节点                    |
| /html/boby/div[@id]           | 选取属于body子节点的带有id属性的div节点              |
| /html/boby/div[@id="content"] | 选取属于body子节点的的id属性值为content的div节点     |
| /html/boby/div[xx>10.00]      | 选取属于body子节点的body子节点的xx元素值大于10的节点 |

## 完整代码

**请运用所学Xpath方法，试着爬取[微博]( https://s.weibo.com/top/summary)的热搜关键词。**

```python
import re
import requests
from lxml import etree

```

```python
# 指定url
url = 'https://s.weibo.com/top/summary'

# user-agent伪装
header = {
    'user-agent':'xxxxxxxxxxxxxx',
    'cookie':'xxxxxxxxxxx'
}
```

```python
requests_get = requests.get(url=url,headers=header)
html = requests_get.content.decode('utf-8')

html = etree.HTML(html,parser=etree.HTMLParser(encoding='utf-8'))
html
```

**<Element html at 0x7fd20ac93f00>**

```python
result = html.xpath('//*[@id="pl_top_realtimehot"]/table/tbody/tr[1]/td[2]/a/text()')
result
```

**['新闻发布会']**

```python
# divs = html.xpath('/html/body/div[1]/div[2]/div/div[2]/div[1]/table/tbody/')
# dics = html.xpath('//*[@id="pl_top_realtimehot"]/table/tbody/tr/td/a')
divs = html.xpath('/html/body/div/div/div/div/div/table/tbody/tr/td/a')
i = 1
for div in divs:
    print("第{}条".format(i),div.text)
    i+=1
```

**第1条 新闻发布会**
**...**
**第19条 LGD**
**第20条 将盆栽越坐越歪的猫咪**
**第21条 活得还没10后小朋友明白**
**第22条 林志颖车祸后首次露面**
**第23条 哄睡师包月套餐标价1.8万**
**第24条 内娱国风氛围感大赏**
第25条 王一博骑摩托艇把街舞导演甩水里了**



# 使用Beautiful Soup库解析网页

**Beautiful Soup 是一个可以从HTML 或 XML 文件中提取数据的python库**

## 完整代码

```python
import requests
from bs4 import BeautifulSoup
from lxml import etree
```

```python
header = {
    'User-Agent': 'Mozilla/x.0 (Windows NT 10.0; Win64; x64) AppleWebKit/xxxxxx (KHTML, like Gecko) Chrome/90.0.4430.85 Safari/xxx.36 Edg/9x.0.xxxx.x6',
    'Cookie': "SUB=_2AkMUH_xxxxxxxxx-yT9jqm8GtRB6P5_ZTJnjeloNEw4vOcUYn5Ft-q_jepMk; SUBP=0033WrSXqPxfM72-Ws9jqgMF5xxxxxxxxoQ4SDwJCdCGAo7QWv7g; _s_tentry=passport.weibo.com; Apache=9820xxxxxxxxx9.3xx.166xxxxxxx5834; SINAGLOBAL=9820789867589.398.1xxxxxx5834; ULV=166xxxxxx835:1:1:1:98207xxxxx589.398.1665366xxxxx4:"}
res = requests.get("https://s.weibo.com/top/summary", headers=header)
```

```python
soup = BeautifulSoup(res.text)
```

```python
dom = etree.HTML(str(soup))
hot_titles = dom.xpath('//*[@id="pl_top_realtimehot"]/table/tbody/tr/td/a')
for i, v in enumerate(hot_titles):
    print(i, v.text)
```

**0 xxxx大会**
**1 商场回应影院不让带蜜雪冰城**
**2 PDD已起诉多人侵犯名誉权**
**3 中国人的书信有多美**
**4 韩剧继承者们首播9周年**
**5 iPhone14车祸检测坐过山车会报警**
**6 教育局回应中学收20元树叶费**
**7 抑郁症不是简单的坏心情**
**8 普京称克里米亚大桥爆炸是恐怖主义行为**
**9 男孩得胃病竟因妈妈染幽门螺杆菌**
**10 未来三个月17.1%受访居民打算购房**
**11 RNG对战CFO**
**12 爱的二八定律出品方没有嘉行**
**13 内蒙古增本土确诊119例无症状559例**
**14 苏炳添再次起诉新东方子公司侵权**
**15 女子吐槽丈夫脑袋掉色枕头焦黄**
**16 女子路边发现80年代供销社**
**17 RNG战胜CFO**

# 使用post请求方法实现登录

**post请求方法能够保障用户端提交数据的安全性，因此被一般需要登录的完整所采用。requests库的post函数能够以post请求方法向服务器发送请求，返回一个Response<Respinse>对象**

## 完整代码

```python
import requests
import matplotlib.pyplot as plt
```

```python
# requests.post(url,data=,json=,**kwargs)
url = 'http://www.ptpress.com.cn/login'
# username: xxxxxxxxxx
# password: xxxxxxxxxx
# verifyCode: 
code_url = 'https://www.ptpress.com.cn/kaptcha.jpg' #验证码
```

```python
#Session会话
sess = requests.Session()
rq_code = sess.get(code_url)    #对验证码的页面进行请求发送
with open('./captcha.jpg','wb') as fp:
    fp.write(rq_code.content)
```

```python
def get_code(): 
    pic = plt.imread('./captcha.jpg')
    plt.imshow(pic)
    plt.show()
    return input('请输入验证码>>>')
```

```python
code = get_code()
```

```python
login_data = {'username':'xxxxxxxxxxx','password':'xxxxxxxxxxx','verifyCode':code}
login_data
```

```python
rq = sess.post(url,data=login_data)
```

**最后一步验证是否成功：https://www.ptpress.com.cn/login：**

```python
print(rq.url)
```

