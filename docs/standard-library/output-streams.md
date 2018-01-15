---
title: "输出流 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: output streams
ms.assetid: b49410e3-5caa-4153-9d0d-c4266408dc83
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f8fee8ecffda86f306b44f0d5b873d5192d4d181
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="output-streams"></a>输出流
输出流对象是字节的目标。 三个最重要的输出流类为 `ostream`、`ofstream` 和 `ostringstream`。  
  
 `ostream` 类通过派生类 `basic_ostream` 支持预定义的流对象：  
  
-   `cout` 标准输出  
  
-   具有有限缓冲的 `cerr` 标准错误  
  
-   `clog` 类似于 `cerr`，但具有完全缓冲  
  
 很少从 `ostream` 构造对象；通常使用预定义的对象。 在某些情况下，可以在启动程序后重新分配预定义的对象。 可配置为缓冲或无缓冲操作的 `ostream` 类最适合于连续的文本模式输出。 基类 `ios` 的所有功能包含在 `ostream` 中。 如果构造 `ostream` 类的对象，则必须指定构造函数的 `streambuf` 对象。  
  
 `ofstream` 类支持磁盘文件输出。 如果需要一个只输出的磁盘，请构造 `ofstream` 类的对象。 在构造 `ofstream` 对象时或在调用该对象的 `open` 成员函数时，可以指定 `ofstream` 对象是否接受二进制或文本模式数据。 许多格式设置选项和成员函数适用于 `ofstream` 对象，包括基类 `ios` 和 `ostream` 的所有功能。  
  
 如果在构造函数中指定文件名，则在构造对象时，将自动打开该文件。 另外，可以在调用默认构造函数后使用 `open` 成员函数。  
  
 类似于运行时函数 `sprintf_s`，`ostringstream` 类支持向内存中的字符串进行输出。 若要通过使用 I/O 流格式设置在内存中创建一个字符串，请构造 `ostringstream` 类的对象。  
  
## <a name="in-this-section"></a>本节内容  
 [构造输出流对象](../standard-library/constructing-output-stream-objects.md)  
  
 [使用插入运算符并控制格式](../standard-library/using-insertion-operators-and-controlling-format.md)  
  
 [输出文件流成员函数](../standard-library/output-file-stream-member-functions.md)  
  
 [缓冲效果](../standard-library/effects-of-buffering.md)  
  
 [二进制输出文件](../standard-library/binary-output-files.md)  
  
 [为自己的类重载 << 运算符](../standard-library/overloading-the-output-operator-for-your-own-classes.md)  
  
 [自行编写无自变量的操控器](../standard-library/writing-your-own-manipulators-without-arguments.md)  
  
## <a name="see-also"></a>请参阅 
 [ofstream](../standard-library/basic-ofstream-class.md)   
 [ostringstream](../standard-library/basic-ostringstream-class.md)   
 [iostream 编程](../standard-library/iostream-programming.md)

