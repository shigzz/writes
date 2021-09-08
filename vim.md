## 前言

每个新奇的想法从程序员的脑海中到眼前的世界，都需要经历文本编辑器的传达。vim作为一个老牌的代码编辑器，在图形化界面成熟以及各种IDE功能丰富的当下，还深受许多程序员的喜爱并为成为编辑器之神。我认为其中最大的原因是，每个vimer手中的vim都可以根据自己的喜好灵活定义，而这种工具自定义的过程不仅能让其更适合自己工作，还能带来额外的快乐。

记得一位大神说过vim的学习过程分为三个阶段：

* 初识vim，没有熟悉vim的一些基本按键操作，会觉得使用起来非常吃力。
* 基本熟练操作vim的一些快捷操作，开始体会到双手不离键盘的爽感。然后开始发现并使用各种各样的插件来武装vim，打造成属于自己的“IDE”。
* 在尝试了众多插件之后，开始思考哪些插件真正可以增加效率，开始根据自己的需要配置插件，同时编写属于自己的script，简化工作流。

我个人非常认同这三阶段，在学习vim之前，我经常在网上看到各种吹vim的声音，于是我打算自己试试，开始自然是非常吃力，到了一些快捷键变成了肌肉记忆之后，我也成为了vim的忠实用户，并真正使用它用于工作。期间只要看到博客中推荐的插件，就安装下来自己试一试。现阶段的我正处在第二阶段到第三阶段的转变中，寻找真正适合自己的插件。

这里主要想分享下自己的vim学习使用经历，分享下自己与工具一起成长的过程。

## 入门篇

这里介绍的是最基础的vim相关的按键，互联网上对于vim基础按键教程的文章数不胜数。在我的印象中，vim的基础操作按键有几十个甚至几百个，只有你想不到没有vim不存在的按键。但是我们需要掌握所有这些按键吗，并不用。就我个人而言，目前操作vim用到的快捷键不超过20个，大频率使用的只有10个左右。

熟练掌握一些快捷按键并且可以流畅地在文本中切换光标时，是我体验到vim爽感的开始。但是这一步是非常难的，在体验到爽感之前，我有好几次想入门vim随后放弃的先例。当你真正决定跳出舒适圈，把vim作为主编辑器使用的时候，才会慢慢把那些按键变成肌肉记忆，最后感受键盘操控光标的快乐。

下面先讲解一下vim主要的三个模式，认识操作模式是熟练基础按键的开端。

| 模式   | 说明                                                   |
| :----- | ------------------------------------------------------ |
| NORMAL | 普通模式，光标的移动，页面的跳转都是在这个模式下进行的 |
| INSERT | 插入模式，编辑模式，在这个模式下愉快地输入吧           |
| VISUAL | 代码块模式，选择代码块进行操作。                       |

下面介绍几个我常用的vim基本按键，掌握一部分部分就可以愉快地操作了。

* 光标移动快捷键

| 按键             | 含义                                    |
| ---------------- | --------------------------------------- |
| h, j, k, l       | 光标向 左/下/上/右 移一个单位           |
| w, b             | 移动到 下/上 一个单词的第一个字符       |
| e, ge            | 移动到 下/上 一个单词的最后一个字符     |
| 0, $, ^          | 移动到 行首/行尾/行第一个字符           |
| gg, G            | 移动到 文件首/文件尾                    |
| H, M, L          | 移动到当前页面的 第一行/中间行/最后一行 |
| [[, ]]           | 移动到 上一个/下一个函数的行首          |
| [], ][           | 移动到 上一个/下一个函数的行尾          |
| f<char>, F<char> | 向后/上跳转到第一个<char>               |

按照上面的表格的内容操作，随便打开一个文本操作一下，是不是体验到快感了。另外，以上跳转命令基本都可以可以结合数字来完成更灵活的操作。比如4h表示向左移动光标4次，5w表示向后跳转5个单词。

* 翻页快捷键

| 按键               | 含义            |
| ------------------ | --------------- |
| <ctrl-d>, <ctrl-u> | 向下/上翻半页   |
| <ctrl-f>, <ctrl-b> | 向下/上翻一页   |
| <ctrl-e>, <ctrl-y> | 向下/上滚动一行 |
