+++
date = '2025-01-10T13:10:24+08:00'
draft = false
title = '命令行工作流'
categories = '命令行'

+++



## 原生命令行快捷键

* 打开默认终端: `ctrl + alt + t`
  * 新建Tab: `ctrl + shift + t`
  * 关闭Tab: `ctrl + shift + w`
  * 新建终端窗口: `ctrl + shift + n`
  * 关闭终端窗口: `ctrl + shift + q`

* 上一条命令: `ctrl + p`
* 下一条命令: `ctrl + n`
* 快速到命令行首: `ctrl + a`
* 快速到命令行尾: `ctrl + e`
* 前进一个字符: `ctrl + f`
* 后退一个字符: `ctrl + b`
* 前进一个单词的长度: `Alt + f`
* 后退一个单词的长度: `Alt + b`
* 清空当前命令: `ctrl + u`
* 清屏, 但是当前打出的命令不消失, 不用写`clear`: `ctrl + l`
* 用编辑器打开当前命令: `ctrl + x, ctrl + e`, 退出后执行命令.
  * 配置默认编辑器: `export EDITOR=vim`



## 快速cd命令

* 一般工作时会频繁进入某些目录, 可以使用某些命令快速`cd`到频繁访问的目录.

* 下载: `conda install -c conda-forge zoxide`.

* 然后配置:

  ```bash
  echo 'eval "$(zoxide init bash)"' >> ~/.bashrc
  source .bashrc
  ```

  



## 查找文件

### find

* Linux原生的命令是`find`:
  * 最常用: `find <路径> -name '*.py'`: 查看某个目录下所有的`.py`文件 (默认递归查找).
  * 模糊查找: `find <路径> -name '*string_name*'`

### fzf

* 一般来说`find`查找出的列表很长, 需要二次搜索, 可以通过管道对接到`fzf`.

* 下载:
  * `apt install fzf`
  * `conda install fzf`



## 查看可执行文件的信息

* 假设你有一个可执行文件`ls`:
  * 查看`ls`的所在目录: `type ls`.
  * 查看系统上到底有多少个`ls`: `type -a ls`.



## `.bashrc`配置

* `cdd`命令: 用`fzf`快速进入目录:

  ```bash
  alias cdd='cd $(find * -type d | fzf)'
  ```


* `v`命令: 用`fzf`快速打开文件:

  ```bash
  alias v='vim $(find * -type d | fzf)'
  ```

  
