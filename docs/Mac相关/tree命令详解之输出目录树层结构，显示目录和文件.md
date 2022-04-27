# tree 命令详解之输出目录树层结构，显示目录和文件

## Linux tree 命令详解（输出目录树层结构，显示目录和文件）

## 一、tree 命令 安装

有些 Linux 可能上面没有 tree 命令，就需要自己来单独安装。

mac 下使用 [brew 包管理工具](./MacOS上快速下载安装brew.md)：

```bash
brew install tree
```

linux 下使用 yum 安装：

```bash
yum install tree
```

## 二、tree 命令怎么使用？

安装成功后，直接在终端使用，使用 --help 查看帮助信息。

```bash
tree --help
```

输出如下：

```bash
➜  ~ tree --help
usage: tree [-acdfghilnpqrstuvxACDFJQNSUX] [-L level [-R]] [-H  baseHREF]
	[-T title] [-o filename] [-P pattern] [-I pattern] [--gitignore]
	[--matchdirs] [--metafirst] [--ignore-case] [--nolinks] [--inodes]
	[--device] [--sort[=]<name>] [--dirsfirst] [--filesfirst]
	[--filelimit #] [--si] [--du] [--prune] [--charset X]
	[--timefmt[=]format] [--fromfile] [--noreport] [--version] [--help]
	[--] [directory ...]
  ------- Listing options -------
  -a            All files are listed.
  -d            List directories only.
  -l            Follow symbolic links like directories.
  -f            Print the full path prefix for each file.
  -x            Stay on current filesystem only.
  -L level      Descend only level directories deep.
  -R            Rerun tree when max dir level reached.
  -P pattern    List only those files that match the pattern given.
  -I pattern    Do not list files that match the given pattern.
  --gitignore   Filter by using .gitignore files.
  --ignore-case Ignore case when pattern matching.
  --matchdirs   Include directory names in -P pattern matching.
  --metafirst   Print meta-data at the beginning of each line.
  --info        Print information about files found in .info files.
  --noreport    Turn off file/directory count at end of tree listing.
  --charset X   Use charset X for terminal/HTML and indentation line output.
  --filelimit # Do not descend dirs with more than # files in them.
  -o filename   Output to file instead of stdout.
  ------- File options -------
  -q            Print non-printable characters as '?'.
  -N            Print non-printable characters as is.
  -Q            Quote filenames with double quotes.
  -p            Print the protections for each file.
  -u            Displays file owner or UID number.
  -g            Displays file group owner or GID number.
  -s            Print the size in bytes of each file.
  -h            Print the size in a more human readable way.
  --si          Like -h, but use in SI units (powers of 1000).
  -D            Print the date of last modification or (-c) status change.
  --timefmt <f> Print and format time according to the format <f>.
  -F            Appends '/', '=', '*', '@', '|' or '>' as per ls -F.
  --inodes      Print inode number of each file.
  --device      Print device ID number to which each file belongs.
  ------- Sorting options -------
  -v            Sort files alphanumerically by version.
  -t            Sort files by last modification time.
  -c            Sort files by last status change time.
  -U            Leave files unsorted.
  -r            Reverse the order of the sort.
  --dirsfirst   List directories before files (-U disables).
  --filesfirst  List files before directories (-U disables).
  --sort X      Select sort: name,version,size,mtime,ctime.
  ------- Graphics options -------
  -i            Don't print indentation lines.
  -A            Print ANSI lines graphic indentation lines.
  -S            Print with CP437 (console) graphics indentation lines.
  -n            Turn colorization off always (-C overrides).
  -C            Turn colorization on always.
  ------- XML/HTML/JSON options -------
  -X            Prints out an XML representation of the tree.
  -J            Prints out an JSON representation of the tree.
  -H baseHREF   Prints out HTML format with baseHREF as top directory.
  -T string     Replace the default HTML title and H1 header with string.
  --nolinks     Turn off hyperlinks in HTML output.
  ------- Input options -------
  --fromfile    Reads paths from files (.=stdin)
  ------- Miscellaneous options -------
  --version     Print version and exit.
  --help        Print usage and this help message and exit.
  --            Options processing terminator.
➜  ~
```

### 语法：

`tree [-aACdDfFgilnNpqstux][-I <范本样式>][-P <范本样式>][目录...]`

### 参数说明：

```
-a 显示所有文件和目录。

-A 使用ASNI绘图字符显示树状图而非以ASCII字符组合。

-C 在文件和目录清单加上色彩，便于区分各种类型。

-d 显示目录名称而非内容。

-D 列出文件或目录的更改时间。

-f 在每个文件或目录之前，显示完整的相对路径名称。

-F 在执行文件，目录，Socket，符号连接，管道名称名称，各自加上"*","/","=","@","|"号。

-g 列出文件或目录的所属群组名称，没有对应的名称时，则显示群组识别码。

-i 不以阶梯状列出文件或目录名称。

-L level 限制目录显示层级。

-l 如遇到性质为符号连接的目录，直接列出该连接所指向的原始目录。

-n 不在文件和目录清单加上色彩。

-N 直接列出文件和目录名称，包括控制字符。

-p 列出权限标示。

-P<范本样式> 只显示符合范本样式的文件或目录名称。

-q 用"?"号取代控制字符，列出文件和目录名称。

-s 列出文件或目录大小。

-t 用文件和目录的更改时间排序。

-u 列出文件或目录的拥有者名称，没有对应的名称时，则显示用户识别码。

-x 将范围局限在现行的文件系统中，若指定目录下的某些子目录，其存放于另一个文件系统上，则将该子目录予以排除在寻找范围外。
```

### 用法示例：

输出你的树层目录结构

cd 目标文件夹路径然后 tree 一下，会将该层级下所有文件都遍历了输出，不管层级有多深。

以树状图列出当前目录结构。可直接使用如下命令：

```bash
tree
```

该命令有如下输出结果：

```bash
➜  TMM-eng.github.io git:(main) tree
.
├── 404.html
├── index.html
├── static
│   ├── 1.07f976e1.png
│   ├── 1.1e2e8b56.png
│   ├── 1.abc1b9f3.png
│   ├── 1.e1034b91.gif
│   ├── 2.6c2b4d98.png
│   ├── 2.703f6f07.png
│   ├── 2.7a6935b7.png
│   ├── 2.ec89fef2.gif
│   ├── 3.50ae116d.png
│   ├── 3.597db35a.png
│   ├── 4.53cdf28b.png
│   ├── 5.053987bc.gif
│   ├── 5.5cb9a1f0.png
│   ├── 5.f744666a.png
│   ├── 6.775a1dde.gif
│   ├── 6.a197e7a7.png
│   ├── 7.375f5222.gif
│   ├── 8.7ca759a2.gif
│   ├── JSON.00b00cd2.png
│   ├── VueLazyload.d51a7272.png
│   ├── a标签下载.456cc8fb.png
│   ├── canvas.752ad503.png
│   ├── indexOf-1.0a605fda.png
│   ├── indexOf-2.9c8672fb.png
│   ├── moment.d989d445.png
│   ├── name.044dd085.jpg
│   ├── project.config配置.771b5a2a.png
│   ├── shell-code.fd3df38e.png
│   ├── storage1.2d7d47e7.png
│   ├── storage2.d3b51d22.png
│   ├── table1.70fd67dd.png
│   ├── table2.12e2dda4.png
│   ├── table3.3ea77d95.png
│   ├── table4.ddcf0882.png
│   ├── vuex.e099173d.png
│   ├── xcrun.60c53543.png
│   ├── 预览.e05c0ce3.png
│   ├── 递归1.bd98e183.jpg
│   ├── 下载promise依赖.cb5fb259.png
│   ├── 柱状图.412bcf9e.png
│   ├── 新建云函数.f0c38bd8.png
│   ├── 上传并部署云函数.f77af50b.png
│   └── 小程序性能和体验优化方法.9601454d.png
├── umi.css
└── umi.js

1 directory, 47 files
```

## 三、tree 命令常用技巧

1、我们可以在目录遍历时使用 -L 参数指定遍历层级

```bash
tree -L 2
```

2、如果你想把一个目录的结构树导出到文件 Readme.md ,可以这样操作

```bash
tree -L 2 >README.md //然后我们看下当前目录下的 README.md 文件
```

3、只显示文件夹

```bash
tree -d
```

4、显示项目的层级，n 表示层级数。例：显示项目三层结构，tree -l 3；

```bash
tree -L n
```

5、tree -I pattern 用于过滤不想要显示的文件或者文件夹。比如要过滤项目中的 node_modules 文件夹；

```bash
tree -I "node_modules"
tree -I "node_modules|docs-dist|docs" -C
```
