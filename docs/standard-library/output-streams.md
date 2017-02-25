---
title: "输出流 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "输出流"
ms.assetid: b49410e3-5caa-4153-9d0d-c4266408dc83
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# 输出流
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

输出流对象是个字节的目标。  三个最重要的输出流类是 `ostream`、`ofstream`和 `ostringstream`。  
  
 `ostream` 类，通过派生类 `basic_ostream`，则支持预定义的流对象：  
  
-   `cout` 标准输出  
  
-   与缓冲的受限`cerr` 标准错误  
  
-   `clog` 类似于 `cerr`，但使用的完全缓冲  
  
 对象从 `ostream`少构造；一般使用预定义对象。  在某些情况下，可以在程序启动后分配预定义对象。  `ostream` 类，可用于缓存的或未缓冲的操作配置，最适合于运行情况下文本输出。  基类，`ios`的所有功能，在 `ostream`中。  如果在构造类 `ostream`对象，必须指定为构造函数的 `streambuf` 对象。  
  
 `ofstream` 类支持磁盘文件输出。  如果需要一输出磁盘，请构造对象类 `ofstream`。  可以指定 `ofstream` 对象是否接受二进制或文本方式数据，当构造 `ofstream` 对象，或者调用 `open` 成员函数时对象。  多格式选项和成员函数应用于 `ofstream` 对象，此时，基 `ios` 和 `ostream` 类的所有功能包括在内。  
  
 如果在构造函数指定文件名，自动打开该文件，当在构造对象时。  否则，可以在调用默认构造函数的后面使用 `open` 成员函数。  
  
 与运行时函数 `sprintf_s`，`ostringstream` 类支持到内存输出字符串。  使用格式化 I\/O 流，要在内存中创建一个字符串，请构造对象类 `ostringstream`。  
  
## 本节内容  
 [构造输出流对象](../standard-library/constructing-output-stream-objects.md)  
  
 [使用插入运算符并控制格式](../standard-library/using-insertion-operators-and-controlling-format.md)  
  
 [输出文件流成员函数](../standard-library/output-file-stream-member-functions.md)  
  
 [缓冲效果](../standard-library/effects-of-buffering.md)  
  
 [二进制输出文件](../standard-library/binary-output-files.md)  
  
 [为您自己的类重载 \<\< 运算符](../standard-library/overloading-the-output-operator-for-your-own-classes.md)  
  
 [自行编写无参数的操控器](../standard-library/writing-your-own-manipulators-without-arguments.md)  
  
## 请参阅  
 [\<ostream\> Members](http://msdn.microsoft.com/zh-cn/a5afd034-0e3c-41ee-bbd7-468d9188da1d)   
 [ofstream](../Topic/ofstream.md)   
 [ostringstream](../Topic/ostringstream.md)   
 [basic\_ostream Members](http://msdn.microsoft.com/zh-cn/82e5cc91-7c0c-4950-a8ce-ac779cfbbd93)   
 [iostream 编程](../standard-library/iostream-programming.md)