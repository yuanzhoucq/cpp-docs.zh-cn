---
title: "基本类型的存储 | Microsoft Docs"
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
  - "算术运算 [C++], 类型"
  - "数据类型 [C], 说明符"
  - "数据类型 [C], 存储"
  - "双精度数据类型, 存储"
  - "浮点数字, 存储"
  - "int 数据类型"
  - "整型"
  - "整型, 存储"
  - "long double 关键字 [C], 存储"
  - "long 关键字 [C]"
  - "Short 数据类型"
  - "有符号类型 [C++], 存储"
  - "说明符 [C++], 类型"
  - "存储 [C++], 类型"
  - "存储类型 [C++]"
  - "类型说明符 [C++], 大小"
  - "类型 [C], 算法"
  - "无符号类型 [C++], 存储"
ms.assetid: bd1f33c1-c6b9-4558-8a72-afb21aef3318
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 基本类型的存储
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下表汇总了与每个基本类型关联的存储。  
  
### 基础类型的大小  
  
|类型|存储|  
|--------|--------|  
|`char`、`unsigned char`、**signed char**|1 个字节|  
|**short**、**unsigned short**|2 个字节|  
|`int`, `unsigned int`|4 个字节|  
|**long**、`unsigned long`|4 个字节|  
|**float**|4 个字节|  
|**double**|8 个字节|  
|`long double`|8 个字节|  
  
 C 数据类型属于常规类别。  “整型”包括 `char`、`int`、**short**、**long**、**signed**、`unsigned` 和 `enum`。  “浮点型”包括 **float**、**double** 和 `long double`。  “算术类型”包括所有浮点型和整型。  
  
## 请参阅  
 [声明和类型](../c-language/declarations-and-types.md)