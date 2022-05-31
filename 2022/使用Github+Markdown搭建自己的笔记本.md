有什么东西慢慢偏离了发明者的初衷呢？

如果列个表，或许能绕赤道几周，Github，应该也能算一个。Github本来是专门用来托管代码的一个远程仓库，让开发者们可以发现、分享以及一起开发优秀的软件产品。但是它能托管的并不只有代码，因此你偶尔会发现一些奇奇怪怪的东西混了进来，例如看穿一切的NoCode、中国诗词大全以及程序猿避坑指南等。

这也不奇怪，毕竟Github提供的是一个托管的机制，至于托管的是什么这就交给用户自己了。

偶然的发现，可以把Github是一个非常好的做笔记的软件，食用起来比有道、印象还香。

起因
最近一直在寻找一款做笔记软件，毕竟古人早就发现了“好记性不如烂笔头”这个亘古不变的真理。有时候记录一些琐碎的知识，比如_如何配置Samba服务器、Ubuntu16.04如何编译Caffe_ ，等等，可能很久不用一次，回头再需要的时候你已经忘了，有个笔记可以省去重新检索的烦恼。主要期望有以下几点：

免费（哈哈）；
能放到服务器：自己的电脑是靠不住的，只有本地有的孤本吃枣药丸；
支持Markdown：Markdown是一个可以用普通文本写出结构化文档的标记语言，目前有多种支持Markdown的编辑器，这就使得笔记的显示效果跨平台、跨应用。同样一份文档，不管拿到那里都基本能得到统一的显示效果。永远也不会忘记当初写论文在自己电脑上排版特别精美，一去打印一团乱麻的噩梦，所以统一的显示效果特别重要。
支持足够深的层级结构：方便归类，所有东西都放到一个文件夹里面的结果和什么都没有差不多；
有网页版，不需要下载客户端：自己家里电脑装的Ubuntu，公司Windows+Ubuntu,目前很多桌面软件对Linux支持不好；
支持笔记下载和上传：自己的笔记只能存在于某个平台上这是不能忍的；
支持保存非markdown内容：平时可能偶尔在网上找到一些认为比较好的PDF之类的资料，直接当参考资料，当然自己备份，网上的东西谁知道下一秒它的服务器还在不在；
支持批量上传下载（可选）：方便5、6点的批量操作，万一哪天哪个平台倒了，如果只能一个个操作不得累死。杞人忧天？也许吧；
支持VIM（可选）：解放鼠标的利器啊。
搜寻
按照自己的期望，我开始了一番查找：

印象笔记：网页版不支持Markdown，果断放弃；
有道云笔记：除了第7、8条都满足，但是使用Markdown缺点明显；
OneNote：不支持Markown；
简书：只有一个文档编辑功能，离要求很远；
后面又试了几个，基本没有能打过有道的了。到了这里好像只能选有道云笔记了，但是有道云笔记有个两个缺点：

不支持解析LaTex公式，这个还能接受，毕竟用的不是很多；
需要显示图片的时候，需要先上传图片，然后再分享获得链接再通过![]()标记来显示，这个太麻烦了。并且，由于图片已经被分享出去了，这就存在安全因患了。
都说念念不忘，必有回响。今天看在Github上浏览代码的时候突然想到，能不能通过Github托管一个仓库来实现？细数的下来，期望的1～8点都能满足，后续如果能找到个CHROME VIM插件就完美了。

Github优点显而易见，因为本身已经熟悉了Git的常规操作，上传下载轻而易举。并且由于它核心是Git，可以轻松实现备份，最多写个脚本就好了，毕竟是自己的专业。Github一份、Gitee一份、本地还可以有一份，万一哪天Github真把中国区锁了（毕竟这个魔幻的年份），Gitee还有。如果三份一起丢失，那就是命吧。
另外由于它基于Git，文档一路的变迁都有迹可寻，只要修改提交了，就不用担心后续手贱删除了什么东西。是要.git这个地基还在，我们就能重建家园。

缺点？也一样不支持LaTex、编辑和预览不同步、没有导航栏、不支持在浏览器上拖拉式的调整目录结构，但瑕不掩瑜，而且导航栏问题可以通过Chrome插件解决。

搭建过程
首先，你要有一个Github账号，如果没有https://github.com/ 注册一个。

第二步，登陆并创建一个私有仓库：
i. 点击页面右上方+号选择New epository：

ii. 填写仓库的信息，如名字、简介等。如果你是电脑上已经有了笔记想迁移到Github，注意别勾选Initialize this repo with README。最关键的是勾选Private选项，这样创建的就是个私有仓库，否则你的笔记就是所有人都能查看了：


显示侧边栏：下载安装Chrome插件Octotree。如果无法访问Google extension store的可以到我Github仓库取（见文末链接）。如果是私有仓库需要配置下，添加github token，安装完成后页面就变成了这样：


这样，一个笔记本仓库就创建完成了。

做笔记
进入仓库，点击仓库又上方的Create new file按钮：


输入笔记的名字。斜杠/之前的名字会被当作目录。例如输入ImgOfDeme/demo.md，ImgOfDeme会被当作目录，demo.md才是文件的名字。注意只又后缀是.md结尾的文件点击预览的时候才能被格式化，否则就是一个普通的文本：




填写好名字，就可以开始编辑了：


编辑过程中如果想查看效果，点击编辑框左上角Preview即可查看到格式化的内容：


编辑完成或者编辑过程中想要保存，点击页面最下方Commit a new file即可，描述主要用于概述你本次提交做了啥，可填可不填，毕竟是笔记又不是代码；


上传一个文件的操作也类似。

批操作
批量下载
可能，经过一番积累，你在仓库里已经有了很多笔记，想要批量打包到本地电脑，做备份或者其他。操作也很简单：直接下载ZIP压缩包或者使用命令行克隆仓库到本地。

直接下载ZIP包：点击仓库右上角Clone or download ,在下拉菜单中选择Download ZIP下载完成后解压缩即可。


命令行克隆到本地：同样点击仓库右上角Clone or download ,在下拉菜单中复制所给出的地址，在命令行中输入下面命令，稍后片刻就好了：

# 执行下面命令需要现在本地安装Git
cd /path/to/the/directory/you/want/your/repo/reside
# Windows: cd C:\\your\path or cd D:\\your\path or ......
git clone <paste the address you just copied here>
1
2
3
4
批量上传
批量上传最爽的还是使用Git：

cd /your/note/
# If this repo is cloned from github you don't need to init 
git init
# If this repo is cloned from github you don't need to add remote otherwise you want to push it to another server
# origin is arbitary name, you can replace it with whatever you want, it specify which remote repo you want 
# your repo to be pushed to.
git remote add origin <paste the address you just copied here, you can get it the same way as download>
git add .
git commit -m "<your commit description>"
git push origin master
<enter your github username>
<enter your password>
1
2
3
4
5
6
7
8
9
10
11
12
如果是在浏览器上操作，就点击Upload files按提示操作即可。

Markdown
顺路简单介绍下Markdown语法。其实常用的就那么几个：

标题；
段落；
列表；
图片；
链接；
表格；
引用；
块；
强调。
标题
标题使用#表示，从#到######一共六级，井号月多标题越小，#从一行顶格开始，和标题名字中间用空格分开，例如：

# 这是一号标题
## 这是二号表标题
### 三号
###### 六号
1
2
3
4
显示效果如下：

这是一号标题
这是二号表标题
三号
六号
段落
段落之间通过两个空格+回车 区分，如果一行的结尾直接回车跟下一段，这两段显示的时候其实会显示成同一段。

列表
列表可分为有序列表和无序列表，由于列表与一般的列表相同，通过1.列表1、2. 列表2...这样的方式，无序列表通过星号*、加号+和减号-表示，显示效果都一样，例如：

* item1
+ itme2
- item3
1
2
3
会显示成：

item1
itme2
item3
图片
图片的显示方法感叹号+中括号+括号例如我的[外链图片转存失败,源站可能有防盗链机制,建议将图片保存下来直接上传(img-BjzumNy1-1587285341226)(https://imgconvert机制,建来csdn传(i.cn/aHg0cHMALy91cGxvYWQtaW8-1hZ2VzLmppYW5zaHUuavdXBsb8FkX2ltYWdlcy7yOTU4Njg2LWUyYTRhY2YyNTlmYmNmYTkucG1n?x-oss-process=image/format,png3)]()]]]]显示成下面这样：


链接
链接和图片类似，只要把图片前面的感叹号去掉就行。例如[LLVM,一堆积木的故事](https://www.jianshu.com/p/9ad4abbffac1)会显示成这样：LLVM,一堆积木的故事

表格
表格语法如下：

|表头1|表头2|表头3|
|:-:|:-:|:-:|
|one|two|three|
|four|five|sixsixsix|
1
2
3
4
显示如下

表头1	表头2	表头3
one	two	three
four	five	sixsixsix
引用
应用使用>表示，可以套娃引用，例如：

> 我引用了别人的一段话
>> 我引用了别人引用别人的一段话的一段话
>>> 我引用了别人引用别人引用别人的一段话的一段话的一段话

1
2
3
4
显示效果如下：

我引用了别人的一段话

我引用了别人引用别人的一段话的一段话

我引用了别人引用别人引用别人的一段话的一段话的一段话

块
块，更多的是用在显示代码，它可以保留代码的原是结构，当然，其实任何文本都可以放进去，它使得里面的文本不会被Mardown渲染成特殊显示效果，例如

# Infact I don't need to import anything, just an example
import torch
print('This is how code should be shown')
1
2
3
使用的方法是使用三个连续反引号（`，键盘左上方esc键下方，不是回车键旁边）将待码快包起来，反引号单独一行，顶格。行内的块用单个反引号

强调
斜体：使用两个星号包裹，例如*斜体内容*显示成斜体内容；
粗体：使用两个星号包裹，例如**粗体内容**显示成粗体内容；
斜体+粗体：使用三个星号包裹，例如***斜体+粗体内容***显示成***斜体+粗体内容***。
星号也可以用下划线代码，效果是一样的。

更多
更多更详细的语法请移步https://daringfireball.net/projects/markdown/syntax

总结
这还有啥总结的?唯一的遗憾始终没有找到一款VIM插件。



首发于个人微信公众号TensorBoy。微信扫描上方二维码或者微信搜索TensorBoy并关注，及时获取更多最新文章！
C++ | Python | 推理引擎 | AI框架源码，有一起玩耍的么？

Materials
https://github.com/zmychou/materials-for-sharing/blob/master/tools/Octotree-bkhaagjahfmjljalopjnoealnfndnagc-4.2.1-Crx4Chrome.com.crx
————————————————
版权声明：本文为CSDN博主「SunnyZhou-1024」的原创文章，遵循CC 4.0 BY-SA版权协议，转载请附上原文出处链接及本声明。
原文链接：https://blog.csdn.net/ZM_Yang/article/details/105617607
