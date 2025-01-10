+++
date = '2025-01-10T12:08:18+08:00'
draft = false
title = '大端序和小端序'
categories = '计算机系统'

+++



## 什么是大端序/小端序

* 假设一个32位整数, 用16进制表示为: `0x0A0B0C0D`;
  * 小端序 (big endian): 从低地址到高地址是`0D`, `0C`, `0B`, `0A`.
  * 大端序 (little endian): 从低地址到高地址是`0A`, `0B`, `0C`, `0D`.



## 小端/大端的应用场景

* 小端: 用于内存中数据存储.
* 大端: 用于网络通信(TCP/IP协议), 假设要传输一个数据`0x0A0B0C0D`, 要先传哪个字节?
  * 大端序就先传`0x0A`.



## 判断小端序和大端序的方法

* 方法一: 直接用API

  ```python
  python -c "import sys; print(sys.byteorder)"
  ```

* 方法二: C语言中, 对于一个整数地址, 用`(char*)`强转, 然后解引用:

  ```c
  #include <stdio.h>
  
  int main() {
      int i = 0x11223344;
      char *p = (char *)&i;
      if (*p == 0x44) puts("little endian");
      else puts("big endian");
      return 0;
  }
  
  ```

  
