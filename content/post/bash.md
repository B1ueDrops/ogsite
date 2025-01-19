+++
date = '2025-01-10T13:10:24+08:00'
draft = false
title = 'Bash极简工作流'
categories = '命令行'

+++



## 下载依赖

### zoxide

* 下载:

  ```bash
  conda install -c conda-forge zoxide
  ```

* 在`.bashrc`最后加入配置:

  ```bash
  cat << EOF >> ~/.bashrc
  eval "$(zoxide init bash)"
  EOF
  ```

* 然后在命令行中, 用`zi`命令, 可以用`fzf`对之前进入过的目录进行检索.

### fzf

* 下载:

  ```bash
  # 如果有sudo权限
  sudo apt install fzf
  # 如果没有sudo权限
  conda install -c conda-forge fzf
  ```

* 然后添加配置:

  ```bash
  cat << EOF >> ~/.bashrc
  eval "$(fzf --bash)"
  export FZF_COMPLETION_TRIGGER='**'
  EOF
  ```

### tmux

* 下载:

  ```bash
  sudo apt install tmux
  ```

* `tmux`简单配置:

  ```bash
  cat << EOF > ~/.tmux.conf
  set -g default-terminal "xterm-256color"
  set -g mouse on
  set -g prefix C-a
  set -g mode-keys vi
  bind-key C-a send-prefix
  bind -r Up resize-pane -U 5
  bind -r Down resize-pane -D 5
  bind -r Left resize-pane -L 5
  bind -r Right resize-pane -R 5
  bind r source-file ~/.tmux.conf \; display-message "Config reloaded!"
  EOF
  ```



### bash

* Bash的简单配置:

  ```bash
  cat << EOF >> ~/.bashrc
  set -o vi
  EOF
  ```

  



## 常见用法



### fzf & zoxide

* **快速切换目录:**  `cd **<TAB>`
  * `**`是`fzf`提供的补全特性.
  * `**`只支持若干自定义的命令, 可以通过`complete | grep _fzf`查看.
  * **快速进入历史目录:** 用`zi`命令.



### bash

* **查找历史命令:** `ctrl+r`
* **编辑器编辑命令行:** `ctrl+x, ctrl+e`
  * 如果需要用`vim`, 需要设置`export EDITOR=vim`
* **清空当前命令:** `ctrl+u`
* **清屏: **`ctrl+l`
  * 如果之前打过命令, 那么清屏后之前的编辑的命令不会消失.
* **快速到命令行首: **`ctrl+a`
* **快速到命令行尾: **`ctrl+e`



### tmux

* **前缀键**: `ctrl+a`
* **重新加载配置文件:** `prefix+r`
* **创建窗口:** `prefix+c`
  * **切换到下一个窗口:** `prefix+n`
  * **切换到上一个窗口:** `prefix+p`
  * **切换到刚才的窗口:** `prefix+l`
  * **最大化窗口:** `prefix+z`
  * **打开窗口列表:** `prefix+w`
  * **切换到某一个窗口:** `prefix+0-9`
  * **重命名窗口:** `prefix+,`
* **左右分屏:** `prefix+%`
* **上下分屏:** `prefix+"`
* **切换分屏:** `prefix+方向键`
* **Copy Mode:**
  * 进入Copy Mode: `prefix+[`
  * 用vi选择复制区域, 用Enter复制.
  * 用`prefix+]`粘贴.
