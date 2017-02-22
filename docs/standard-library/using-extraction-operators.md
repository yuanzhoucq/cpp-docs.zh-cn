---
title: "使用提取运算符 | Microsoft Docs"
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
  - ">> 运算符, 提取运算符"
  - "提取运算符"
  - "运算符 [C++], 提取"
ms.assetid: a961e1a9-4897-41de-b210-89d5b2d051ae
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 使用提取运算符
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

提取运算符 \(`>>`\)，为所有标准 C\+\+ 数据类型。预编程序，很容易方法输入流对象获取字节。  
  
 格式化文本提取输入运算符由空格分隔的数据值。  这很不方便，在文本字段包含多个单词时，或者当逗号分隔数字时。  在这种情况下，一种方法是使用非格式化的类型成员读取具有函数 [istream::getline](../Topic/basic_istream::getline.md) 中的空白的文本块，然后分析具有特殊功能块。  另一种方法是派生具有成员函数的输入流类，如 `GetNextToken`istream 可以调用成员提取和格式字符数据。  
  
## 请参阅  
 [输入流](../standard-library/input-streams.md)