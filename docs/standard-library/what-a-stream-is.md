---
title: "流的定义 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- reading data [C++], iostream programming
- data [C++], reading
- streams [C++], in iostream classes
- streams [C++]
ms.assetid: a7e661e9-6cd1-4543-a9a4-c58ee9fd32f3
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 75c23582cbbb42a417a7a5effdb879300c2a7732
ms.lasthandoff: 02/24/2017

---
# <a name="what-a-stream-is"></a>流的定义
与 C 类似，C++ 不具有内置输入/输出功能。 但是，所有 C++ 编译器都捆绑了一个系统的、面向对象的 I/O 包，称为 iostream 类。 该流是 iostream 类中的核心概念。 可将流对象视为一个智能文件，此文件充当字节的源和目标。 流的特征由其类和自定义的插入和提取运算符确定。  
  
 通过设备驱动程序，磁盘操作系统可将键盘、屏幕、打印机和通信端口作为扩展文件来处理。 iostream 类与这些扩展文件进行交互。 内置类支持使用与磁盘 I/O 相同的语法写入内存或从中读取，从而可以轻松派生流类。  
  
## <a name="in-this-section"></a>本节内容  
 [输入/输出替换选项](../standard-library/input-output-alternatives.md)  
  
## <a name="see-also"></a>另请参阅  
 [iostream 编程](../standard-library/iostream-programming.md)


