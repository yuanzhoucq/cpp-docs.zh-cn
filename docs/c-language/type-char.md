---
title: "char 类型 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "char 关键字 [C]"
  - "char 类型"
  - "无符号 char 关键字 [C]"
ms.assetid: a5da0866-e780-4793-be87-15a8426e7ea0
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# char 类型
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`char` 类型用于存储可表示的字符集的成员的整数值。  该整数值是与指定字符对应的 ASCII 代码。  
  
 **Microsoft 专用**  
  
 类型 `unsigned char` 的字符值的范围介于 0 和 0xFF（十六进制）之间。  **signed char** 的范围介于 0x80 和 0x7F 之间。  这些范围分别转换为 0 到 255（十进制）以及 –128 到 \+127（十进制）。  \/J 编译器选项将默认值从 **signed** 更改为 `unsigned`。  
  
 **结束 Microsoft 专用**  
  
## 请参阅  
 [基本类型的存储](../c-language/storage-of-basic-types.md)