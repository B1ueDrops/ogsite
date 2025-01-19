+++
date = '2025-01-19T13:47:16+08:00'
draft = false
title = 'pdb调试python命令'

+++



## 下载依赖

* `pudb`:

  ```bash 
  pip install pudb
  ```

  

## 开始调试



### 修改源代码

* 首先设置环境变量, 用`pudb`替换原版的`pdb`:

  ```bash
  export PYTHONBREAKPOINT="pudb.set_trace"
  ```

* 可以在你的源代码中, 加入一行`breakpoint()`.

* 然后用`python`直接运行, 会自动停下.

  

### 不修改源代码

* 直接使用`python3 -m pudb main.py`运行.



## 调试命令

