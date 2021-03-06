# gitignore 配置

## .gitignore 配置

一、简介我们做的每个 Git 项目中都需要一个“.gitignore”文件，这个文件的作用就是告诉 Git 哪些文件不需要添加到版本管理中。比如我们项目中的 npm 包(node_modules)，它在我们项目中是很重要的，但是它占的内存也是很大的，所以一般我们用 Git 管理的时候是不需要添加 npm 包的。

语法规范空行或是以#开头的行即注释行将被忽略。可以在前面添加正斜杠/来避免递归,下面的例子中可以很明白的看出来与下一条的区别。可以在后面添加正斜杠/来忽略文件夹，例如 build/即忽略 build 文件夹。可以使用!来否定忽略，即比如在前面用了\*.apk，然后使用!a.apk，则这个 a.apk 不会被忽略。

用来匹配零个或多个字符，如.[oa]忽略所有以".o"或".a"结尾，\*忽略所有以结尾的文件（这种文件通常被许多编辑器标记为临时文件）；[]用来匹配括号内的任一字符，如[abc]，也可以在括号内加连接符，如[0-9]匹配 0 至 9 的数；?用来匹配单个字符。举个栗子：

```
# 忽略 .a 文件
*.a
# 但否定忽略 lib.a, 尽管已经在前面忽略了 .a 文件
!lib.a
# 仅在当前目录下忽略 TODO 文件， 但不包括子目录下的 subdir/TODO
/TODO
# 忽略 build/ 文件夹下的所有文件
build/
# 忽略 doc/notes.txt, 不包括 doc/server/arch.txt
doc/*.txt
# 忽略所有的 .pdf 文件 在 doc/ directory 下的
doc/**/*.pdf
```

二、常用的规则

```
/mtk/ 过滤整个文件夹
*.zip 过滤所有.zip文件
/mtk/do.c 过滤某个具体文件
```

以上规则意思是：被过滤掉的文件就不会出现在你的 GitHub 库中了，当然本地库中还有，只是 push 的时候不会上传。除了以上规则，它还可以指定要将哪些文件添加到版本管理中。

```
!src/   不过滤该文件夹
!*.zip   不过滤所有.zip文件
!/mtk/do.c 不过滤该文件
```

1、配置语法：

- 以斜杠/开头表示目录；
- 以星号\*通配多个字符；
- 以问号?通配单个字符
- 以方括号[]包含单个字符的匹配列表；
- 以叹号!表示不忽略(跟踪)匹配到的文件或目录；

此外，git 对于 .ignore 配置文件是按行从上到下进行规则匹配的，意味着如果前面的规则匹配的范围更大，则后面的规则将不会生效；

2、示例说明 a、规则：fd1/_ 说明：忽略目录 fd1 下的全部内容；注意，不管是根目录下的 /fd1/ 目录，还是某个子目录 /child/fd1/ 目录，都会被忽略； b、规则：/fd1/_ 说明：忽略根目录下的 /fd1/ 目录的全部内容； c、规则： /\* !.gitignore !/fw/bin/ !/fw/sf/ 说明：忽略全部内容，但是不忽略 .gitignore 文件、根目录下的 /fw/bin/ 和 /fw/sf/ 目录；

3、创建.gitignore 文件 1)常规的 windows 操作

- 根目录下创建 gitignore.txt；
- 编辑 gitignore.txt，写下你的规则，例如加上 node_modules/；
- 打开命令行窗口，切换到根目录（可以直接在文件夹上面的地址栏输入 cmd 回车）；
- 执行命令 ren gitignore.txt .gitignore。

  2)用 Git Bash

- 根目录下右键选择“Git Bash Here”进入 bash 命令窗口；
- 输入 vim .gitignore 或 touch .gitignore 命令，打开文件（没有文件会自动创建）；
- 按 i 键切换到编辑状态，输入规则，例如 node_modules/，然后按 Esc 键退出编辑，输入:wq 保存退出。

如下：

```
# dependencies  npm包文件
/node_modules

# production  打包文件
/build

# misc
.DS_Store

npm-debug.log*
```

.DS_Store：这个文件是 Mac OS X 用来存储文件夹的一些诸如自定义图标，ICON 位置尺寸，窗口位置，显示列表种类以及一些像窗体自定义背景样式，颜色这样的元信息。默认情况下，Mac OS X 下的每个文件夹下应该都会生成一个，包括网络介质存储盘和 U 盘这样的外部设备。

npm-debug.log：项目主目录下总是会出现这个文件，而且不止一个，原因是 npm i 的时候，如果报错，就会增加一个此文件来显示报错信息，npm install 的时候则不会出现。

最后需要强调的一点是，如果你不慎在创建.gitignore 文件之前就 push 了项目，那么即使你在.gitignore 文件中写入新的过滤规则，这些规则也不会起作用，Git 仍然会对所有文件进行版本管理。

简单来说，出现这种问题的原因就是 Git 已经开始管理这些文件了，所以你无法再通过过滤规则过滤它们。因此一定要养成在项目开始就创建.gitignore 文件的习惯，否则一旦 push，处理起来会非常麻烦。

官网相关配置：[https://help.github.com/cn/articles/ignoring-files](https://help.github.com/cn/articles/ignoring-files)
