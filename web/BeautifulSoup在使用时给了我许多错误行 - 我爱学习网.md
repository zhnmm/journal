我已将beautifulsoup（名为bs4的文件）安装到我的python项目文件夹中，该文件夹与我正在运行的python文件相同。这个py文件包含以下代码，对于输入，我使用这个URL指向一个简单的页面，其中包含一个链接，代码应该检索该链接。

用作URL输入的URL:http://data.pr4e.org/page1.htm

.py code:

```
import urllib.request, urllib.parse, urllib.error
from bs4 import BeautifulSoup
import ssl

ctx = ssl.create_default_context()
ctx.check_hostname = False
ctx.verify_mode = ssl.CERT_NONE

url = input('Enter - ')
html = urllib.request.urlopen(url, context=ctx).read()
soup = BeautifulSoup(html, 'html.parser')


tags = soup('a')
for tag in tags:
    print(tag.get('href', None))
```

虽然我可能错了，但在我看来bs4导入是正确的，因为我的IDE程序在我开始键入它时建议使用BeautifulSoup。毕竟，它安装在与服务器相同的目录中。py文件。但是，当我使用前面提供的url运行它时，它会抛出以下几行错误：

```
Traceback (most recent call last):
  File "C:\Users\Thomas\PycharmProjects\pythonProject\main.py", line 16, in <module>
    soup = BeautifulSoup(html, 'html.parser')
  File "C:\Users\Thomas\PycharmProjects\pythonProject\bs4\__init__.py", line 215, in __init__
    self._feed()
  File "C:\Users\Thomas\PycharmProjects\pythonProject\bs4\__init__.py", line 241, in _feed
    self.endData()
  File "C:\Users\Thomas\PycharmProjects\pythonProject\bs4\__init__.py", line 315, in endData
    self.object_was_parsed(o)
  File "C:\Users\Thomas\PycharmProjects\pythonProject\bs4\__init__.py", line 320, in 
object_was_parsed
    previous_element = most_recent_element or self._most_recent_element
  File "C:\Users\Thomas\PycharmProjects\pythonProject\bs4\element.py", line 1001, in __getattr__
    return self.find(tag)
  File "C:\Users\Thomas\PycharmProjects\pythonProject\bs4\element.py", line 1238, in find
    l = self.find_all(name, attrs, recursive, text, 1, **kwargs)
  File "C:\Users\Thomas\PycharmProjects\pythonProject\bs4\element.py", line 1259, in find_all
    return self._find_all(name, attrs, text, limit, generator, **kwargs)
  File "C:\Users\Thomas\PycharmProjects\pythonProject\bs4\element.py", line 516, in _find_all
    strainer = SoupStrainer(name, attrs, text, **kwargs)
  File "C:\Users\Thomas\PycharmProjects\pythonProject\bs4\element.py", line 1560, in __init__
    self.text = self._normalize_search_value(text)
  File "C:\Users\Thomas\PycharmProjects\pythonProject\bs4\element.py", line 1565, in _ 
normalize_search_value
    if (isinstance(value, str) or isinstance(value, collections.Callable) or hasattr(value, 
'match')
AttributeError: module 'collections' has no attribute 'Callable'

Process finished with exit code 1
```

错误消息中引用的行来自bs4中作为其一部分下载的文件。我没有编辑过任何包含bs4的文件，甚至没有碰过它们。有人能帮我弄清楚为什么bs4不工作吗？