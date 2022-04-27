# Mac 显示隐藏文件

`defaults write com.apple.finder AppleShowAllFiles -bool true`

# 关闭显示隐藏文件夹功能:

`defaults write com.apple.finder AppleShowAllFiles -bool false`

---

命令输入后重启 Finder 应用（即访达）：command+option+esc 找到访达 点击重新开启

# 2022-04-27

# Mac 显示隐藏文件或者文件夹

1、通过快捷键 ￼Command+Shift+. 可以显示隐藏文件、文件夹，再按一次，恢复隐藏 2、通过终端命令来显示或隐藏在终端（Terminal）输入如下命令，即可显示隐藏文件和文件夹

```bash
defaults write com.apple.finder AppleShowAllFiles -boolean true; killall Finder
```

如需再次隐藏原本隐藏的文件和文件夹，可以输入如下命令

```bash
defaults write com.apple.finder AppleShowAllFiles -boolean false ; killall Finder
```

3、通过终端来查找

打开终端，进入到要找的隐藏文件目录下，输入：，就可以看到所有的文件，包括隐藏

### 参考：

《macOS 使用手册》在 Mac 上显示或隐藏文件扩展名 https://support.apple.com/zh-cn/guide/mac-help/mchlp2304/mac
