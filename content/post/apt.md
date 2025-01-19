+++
date = '2025-01-19T15:45:21+08:00'
draft = false
title = 'apt的正确使用方式'
+++



## 下载依赖

* `apt-file`

  ```bash
  sudo apt install apt-file
  sudo apt-file update
  ```

  

## 常见用法

* **查看一个包是否可以被下载:**

  ```bash
  apt show <package-name>
  ```

* **查看某个包的依赖:**

  ```bash
  apt depends <package-name>
  ```

* **下载某个包:**

  ```bash
  sudo apt install <package-name>
  ```


* **查看某个包到底有哪些文件, 放在哪些位置:**

  ```bash
  apt list <package-name>
  ```

  

* **更新系统中的所有包:**

  ```bash
  sudo apt upgrade
  ```

* **更新某个包:**

  ```bash
  sudo apt install --only-upgrade <package-name>
  ```

* **已知一个文件(一般是.so依赖库), 查找它归属的package, 支持模糊搜索**

  ```bash
  apt-file search libgthread-2.0.so.0
  ```
