## 前言

每个新奇的想法从程序员的脑海中到眼前的世界，都需要经历文本编辑器的传达。vim作为一个老牌的代码编辑器，在图形化界面成熟以及各种IDE功能丰富的当下，还深受许多程序员的喜爱并称之为编辑器之神。我认为其中最大的原因是，每个vimer手中的vim都可以根据自己的喜好灵活定义，工具自定义的过程不仅能让其更适合自己工作，还能在工具越来越顺手的过程中收获满足感。快捷键+命令的编辑模式本身也是一种编程，使用vim开发可以同时享受两种编程带来的爽感。

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

| 按键                 | 含义                                    |
| -------------------- | --------------------------------------- |
| h, j, k, l           | 光标向 左/下/上/右 移一个单位           |
| w, b                 | 移动到 下/上 一个单词的第一个字符       |
| e, ge                | 移动到 下/上 一个单词的最后一个字符     |
| 0, $, ^              | 移动到 行首/行尾/行第一个字符           |
| gg, G                | 移动到 文件首/文件尾                    |
| H, M, L              | 移动到当前页面的 第一行/中间行/最后一行 |
| [[, ]]               | 移动到 上一个/下一个函数的行首          |
| [], ][               | 移动到 上一个/下一个函数的行尾          |
| f\<char\>, F\<char\> | 向后/上跳转到第一个\<char\>             |

按照上面的表格的内容操作，随便打开一个文本操作一下，是不是体验到快感了。另外，以上跳转命令基本都可以可以结合数字来完成更灵活的操作。比如4h表示向左移动光标4次，5w表示向后跳转5个单词。

* 翻页快捷键

| 命令                   | 含义            |
| ---------------------- | --------------- |
| \<ctrl-d>, \<ctrl-u\>  | 向下/上翻半页   |
| \<ctrl-f\>, \<ctrl-b\> | 向下/上翻一页   |
| \<ctrl-e\>, \<ctrl-y\> | 向下/上滚动一行 |

* 文本编辑快捷键（涉及NORMAL模式 <-> INSERT模式）

| 命令    | 含义                                         |
| ------- | -------------------------------------------- |
| \<esc\> | 插入模式切换到普通模式                       |
| i, a, A | 在 光标处/光标后/行尾 插入，并切换到插入模式 |
| o, O    | 在 上一行/下一行 新开一行，并切换到插入模式  |
| yy, dd  | 复制/剪切 当前行                             |
| yw, dw  | 复制/剪切 光标后面的一个单词                 |
| yb, db  | 复制/剪切 光标前面的一个单词                 |
| x       | 删除当前光标的一个字符                       |
| p       | 在当前行之后粘贴缓冲寄存器的内容             |
| P       | 在当前行之前粘贴缓冲寄存器的内容             |

同样这个快捷键也可以结合数字来达到更牛逼的效果，比如3dd表示删除3行

* 其他命令

| 命令                 | 含义                                    |
| -------------------- | --------------------------------------- |
| :q, :w, :wq          | 退出，保存文件，保存文件并退出          |
| :q!                  | 强制退出（丢弃未保存的内容）            |
| :e \<filename\>      | 打开一个文件（没有则新建）              |
| :tab \<filename\>    | 在一个新tab中打开一个文件（没有则新建） |
| :sp, :vsp            | 竖向/横向分屏                           |
| /\<word\>, ?\<word\> | 向后/向前搜索单词word                   |
| *, #                 | 向后/向前搜索当前光标在的单词           |
| n, N                 | 跳转光标到后一个/前一个搜索词           |

掌握以上命令，你已经可以处理并编写一些简单的文件了，并且已经感受到一些操作的精妙性。上述命令我忽略了regs，tabs，marks等机制，可以自行探索～

但是要使用vim写代码，这些肯定是不够的，如果上述命令熟练后，可以进去第二部分，真正让vim爽的一部分要来了，准备好感受自定义的快乐吧。

## 配置与插件篇

### vimscript

vimscript是vim提供的插件语言，通过vimscript可以修改，配置vim的参数，甚至插件的开发。具体教程如下：<https://zhuanlan.zhihu.com/p/37352209>

### vimrc

vimrc便是编写vimscript的地方，在vim启动的时候会自动加载vimrc文件中的配置。vim的vimrc路径一般为`~/.vimrc`；如果是neovim，那么对应的vimrc为`~/.config/neovim/init.vim`。以我目前配置的vimrc为例，作一些简单的讲解。

```vimscript
set history=500
set nocompatible "兼容性设置
set hlsearch "高亮设置
set cmdheight=1
set nu "显示行号

filetype plugin on
filetype indent on

"mapleader，对应之后的<leader>，有大作用
let mapleader=";" 

set ts=4
set sw=4

" key mapping
map <leader>w :w<cr>  " map a b 将a映射到b，用于自定义按键
map <leader>q :q<cr>

inoremap <leader>a <ESC> " inoremap中，i表示在insert模式下，nore表示不能递归map
inoremap <leader>w <ESC>:w<cr> 
inoremap <c-l> <ESC>la " insert模式下将光标右移

"vim中使用<C-W>j/k/h/l实现窗口间的跳转，以下映射简化了这些快捷键
map <C-j> <C-W>j
map <C-k> <C-W>k
map <C-h> <C-W>h
map <C-l> <C-W>l
```

### 插件

了解了vimscript之后，你可能会想，是否可以通过编写vimcript来扩展vim的功能。没错，vim的插件就是基于这个想法，通过vimscript来实现定制化的功能。在学习vim的过程中，发现一个插件，安装并使用，绑定自定义的快捷键，甚至自己写一个插件，都会是飞速提升vim使用体验的事情。

从获取插件开始，如同系统软件包管理一样，vim也有插件包管理器，目前体验最好的是[vim-plug](https://github.com/junegunn/vim-plug)，根据其github页面提供的说明，首先安装vim-plug：

```shell
curl -fLo ~/.vim/autoload/plug.vim --create-dirs \
    https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim
```

`~/.vim`文件夹是保存vim插件及配置的文件夹，该命令将vim-plug自动化的命令安装到该目录的`autoload`文件夹下，每次vim启动时会加载。

之后在.vimrc配置文件中，加入以下代码：

```
...

call plug#begin('~/.vim/plugged')
Plug 'XXX'
Plug 'XXX'
call plug#end()

...

```

接下来，安装插件的步骤非常简单，如果你在github上找到了一个有意思的插件，想要添加到自己的vim中，只需要在上述代码的两个call之间添加一行，其中的XXX替换为这个插件的名称，以著名的NerdTree插件为例，这个插件可以在vim上提供文件管理器的功能。在github上找到了该插件的地址：<https://github.com/preservim/nerdtree>，在vimrc的上述代码区域中添加一行`Plug 'preservim/nerdtree'`，便表示将该插件添加到vim中。几乎所有可以在github上找到的插件，都可以使用上述方法添加。

将需要的插件声明到vimrc之后，保存vimrc退出之后再重启vim。执行`:PlugInstall`命令安装之前声明的插件，该命令会检查`~/.vim/plugged`下的插件是否已经在vimrc中声明，如果不存在，就从github仓库拉取最近的分支。

## 工作流搭建

说了这么多，那么进入正题，怎么使用vim搭建出适合开发使用的环境呢。这之前我省略了推荐插件那一部分，但是插件本身是为了配合我们的工作流使用，那么就顺势通过一边搭建环境一边介绍插件。

### Golang

由于目前我工作中主要使用Golang，而Golang又是一门足够简单的语言，使得它特别适合使用vim来进行开发（不会像C/C++在使用过程中会遇到很多的坑）。下面，就跟随我一步一步打造属于gopher专属的vim环境，立志达到秒杀IDE的体验。

#### [vim-go](https://github.com/fatih/vim-go)

<img src="https://github.com/fatih/vim-go/blob/master/assets/vim-go.png?raw=true">



vim-go是使用vim开发Golang中最重要的插件，使用vim-go配合gopls等相关工具可以完成几乎所有Go程序的跳转，补全，分析等功能。通常在IDE上，我们需要通过点鼠标完成的操作，使用vim-go，只需要敲命令即可完成上述工作。如果你嫌敲命令麻烦，那么你可以绑定属于自己的快捷键映射，使用快捷键组合替代命令，达到更快的效率提升。

安装过程只需要将`Plug 'fatih/vim-go'` 这一行代码加入到vimrc的插件声明中，安装完插件后打开vim，然后输入`:GoInstallBinaries`，该命令会向`$GOPATH/bin`中添加go开发相关的工具，比如`goimports`，`gopls`，`govet`，`dlv`等工具。

介绍几个我用得比较多的命令吧：

* `:GoImplements`列出某个接口的实现列表，或者跳转到某个结构体对应的接口
* `:GoCallers`列出某个函数的调用者
* `:GoCallees`与上一个相反，列出函数的调用对象
* `:GoReferrers`列出与某个变量（包括函数）相关的代码行

此外，与编译相关的`:GoBuild`，测试相关的`:GoTest`，调试相关的`:GoDebugXXX`等就不在这儿多介绍了，vim-go是个功能非常全面的插件，等待有兴趣的朋友去读文档了解。

#### [YouCompleteMe](https://github.com/ycm-core/YouCompleteMe)

YouCompleteMe（简称ycm）非常强大的一个语言辅助工具，结合不同的lsp给不同的语言提供全面的代码跳转，补全，错误检测等等功能，个人认为是同类插件中使用最好的，据说也是安装过程最困难的一个插件。

可能有朋友注意到，vim-go也能提供lsp相关的功能，ycm的功能和vim-go发生了重叠。确实，而且ycm和vim-go使用的lsp工具都是gopls，同时使用还会造成重复资源的浪费。因为ycm提供多种语言的辅助功能，而且体验上比较优秀，同时除了Golang开发外，我也需要使用vim开发C/C++/Python等语言，都会使用到ycm。所以，我选择了ycm，在vim-go中禁用了gopls，仅保留了基础功能，如代码块的跳转。（如果是在内存方面“财大气粗”的朋友可以不用理会，两者都开启）。

**那么就开始最艰难的插件的安装过程吧**

首先在`.vimrc`文件中添加`Plug 'Valloric/YouCompleteMe'`，保存并重启vim，执行`:PlugInstall`安装，ycm的包比较大，还有一些子模块，拉取的时间有点慢，甚至有时会因为timeout而失败。这时候如果你有万物互联的工具，可以配置一下git代理，提升成功率。

因为ycm需要python3环境，所以首先得确保你的vim版本支持。如何检查当前的vim版本是否支持python3呢，可以使用`vim --version | grep python3`命令，如果python3前面的符号为`+`，那么恭喜，你的vim支持，直接跳到ycm配置吧，如果是`-`，我们需要另外配置。

如果你使用的vim不支持python3的插件，在启动vim的时候可能会收到如下警告：

```
YouCompleteMe unavailable: requires Vim compiled with Python (3.6.0+) support.
```

根据提示，如果需要正常运行ycm，需要确保两件事：首先，你电脑上的python版本必须大于3.6.0；其次，你的vim需要支持python3的插件。

如果python版本不符合要求，那就把python版本升级下，这里就不多做赘述。第二种情况或许更为常见，如果系统的包管理器更新的vim都不支持python3，那么可以采用以下两种解决方法。

1. 重新编译vim，在配置编译参数时开启python3支持，除此之外，你还可以选择是否开启其他语言的支持，比如ruby，lua。具体做法可以参考：<https://www.jianshu.com/p/aac78ff576c5>
2. 使用homebrew包管理器安装vim。macOS和Linux都可以使用homebrew，根据个人经验，使用brew安装的vim都默认支持python3。该方法比较简单快捷，个人推荐这个方法。

这一步结束之后，ycm的插件安装过程到了最关键的步骤，但是没有之前那么多的坑了。那么就一鼓作气，将它装完。

进入ycm的文件夹：`.vim/plugged/YouCompleteMe`，可以看到该目录下有个`install.py`文件，安装过程只需要执行这个文件就行。`install.py`有多个选项，分别对应不同的语言安装不同的lsp，主要有以下几个：

* --clang-completer，C家族的语言辅助引擎
* --clangd-completer，同样是C家族的辅助工具，但是采用clangd作为lsp server
* --cs-completer，C#
* --go-completer，Golang
* --rust-completer，rust
* --java-completer，没错，它也支持Java
* --ts-completer，TypeScript和JavaScript

由于是Golang的开发环境，因此我们只要选择一个就行：

```
python3 install.py --go-completer
```

如果中间出现了编译库不存在的问题，那么根据报错信息安装对应的库即可。还有一种失败的情况——编译器不支持C++17也会导致编译失败，需要升级一下你的GNU套件。

好了，以上顺利完成后，整个ycm的安装已经完成了，最后只需要在`.vimrc`文件中配置一下，就可以开启代码跳转，补全的快乐了。

**安装完毕，开始爽**

在Golang项目代码中，一般对于某个变量/函数/结构的跳转需求，我主要依赖三个：

* 跳转到当前变量/函数/结构的定义
* 列出当前变量/函数/结构相关代码的列表
* 跳转到当前结构实现的接口/列出实现了某个接口的所有结构

这三个需求使用ycm都可以实现。使用以下命令分别对应于上述的三个跳转需求:

* `:YcmCompleter GoToDefinitionElseDeclaration`
* `:YcmCompleter GoToReferences`
* `:YcmCompleter GoToImplementation`

当然，在开发中，我们使用跳转命令的频次是非常高的，如果每次都要敲命令的话，必然不能提高效率。这里同样可以使用映射来自定义快捷键，比如我就将上述三个命令作了如下映射。

```
nnoremap <leader>j :YcmCompleter GoToDefinitionElseDeclaration<CR>
nnoremap <leader>r :YcmCompleter GoToReferences<CR>
nnoremap <leader>i :YcmCompleter GoToImplementation<CR>
```

这里我设置了比较好记的快捷键，`j`代表`jump`,`r`代表`references`，`i`代表`implementation`。大家也可以根据自己的喜好自己定义。

关于ycm另外的设置以及解释，我也在这里给出：

``` 
" 触发补全快捷键
" 向后切换补全候选词
let g:ycm_key_list_select_completion = ['<TAB>', '<c-n>', '<Down>']
" 向前切换补全候选词
let g:ycm_key_list_previous_completion = ['<S-TAB>', '<c-p>', '<Up>']

let g:ycm_auto_trigger = 1
" 最小自动触发补全的字符大小设置为 2
let g:ycm_min_num_of_chars_for_completion = 2
let g:ycm_add_preview_to_completeopt = 0
let g:ycm_show_diagnostics_ui = 0
let g:ycm_server_log_level = 'info'
let g:ycm_min_num_identifier_candidate_chars = 2
let g:ycm_collect_identifiers_from_comments_and_strings = 1
let g:ycm_complete_in_strings=1
let g:ycm_key_invoke_completion = '<c-z>'
" 关闭preview窗口
set completeopt-=preview
```

#### [NerdTree](https://github.com/preservim/nerdtree)



#### [LeaderF](https://github.com/Yggdroot/LeaderF)



#### [AirLine](https://github.com/vim-airline/vim-airline)



#### [Ack](https://github.com/mileszs/ack.vim)



#### [NerdCommenter](https://github.com/preservim/nerdcommenter)



#### [Gitgutter](https://github.com/airblade/vim-gitgutter)
