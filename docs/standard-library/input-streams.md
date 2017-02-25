---
title: "输入流 | Microsoft Docs"
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
  - "数据 [C++], 从输入流中读取"
  - "输入流对象"
  - "输入流"
  - "读取数据 [C++], 从输入流"
ms.assetid: f14d8954-8f8c-4c3c-8b99-14ddb3683f94
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# 输入流
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

输入流源对象是个字节。  三个最重要的输入流、和类为 [istream](http://msdn.microsoft.com/zh-cn/6801779e-260e-416d-b4ec-fef5ff1b2371)[ifstream](../Topic/ifstream.md)[istringstream](../Topic/istringstream.md)。  
  
 `istream` 类最适用于运行文本方式输入使用。  可以配置 `istream` 类缓存对象的或未缓冲的操作。  基类，`ios`的所有功能，在 `istream`中。  基本上不会从 `istream`类的对象。  相反，您通常会使用预定义的 `cin` 对象，实际上是 [ostream](../standard-library/ostream.md)类对象。  在某些情况下，可以将 `cin` 赋予其他流对象在程序启动之后。  
  
 `ifstream` 类支持磁盘文件项。  如果需要对输入磁盘文件，请构造对象类 `ifstream`。  可以指定二进制或文本方式数据。  如果在构造函数指定文件名，则会自动打开文件，当在构造对象时。  否则，可以在调用默认构造函数的后面使用 `open` 函数。  多格式选项和成员函数应用于 `ifstream` 对象。  基 `ios` 和 `istream` 类的所有功能在 `ifstream`中。  
  
 与库函数 `sscanf_s`，`istringstream` 类则支持从内存字符串的项。  若要获取从具有 Null 结束符的字符数组的数据，请分配和初始化字符串，然后构造对象类 `istringstream`。  
  
## 本节内容  
 [构造输入流对象](../standard-library/constructing-input-stream-objects.md)  
  
 [使用提取运算符](../standard-library/using-extraction-operators.md)  
  
 [测试提取错误](../standard-library/testing-for-extraction-errors.md)  
  
 [输入流操控器](../standard-library/input-stream-manipulators.md)  
  
 [输入流成员函数](../standard-library/input-stream-member-functions.md)  
  
 [为自己的类重载 \>\> 运算符](../standard-library/overloading-the-input-operator-for-your-own-classes.md)  
  
## 请参阅  
 [iostream 编程](../standard-library/iostream-programming.md)