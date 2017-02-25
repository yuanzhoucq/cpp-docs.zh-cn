---
title: "数据类型说明符和等效项 | Microsoft Docs"
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
  - "数据类型 [C++], 等效"
  - "数据类型 [C++], 说明符"
  - "标识符, 数据类型"
  - "符号扩展整型"
  - "简单类型, 名称"
  - "类型名称 [C++], 简单"
  - "类型说明符 [C++], 列表"
  - "扩大整数"
  - "零扩展"
ms.assetid: 0d4b515a-4f68-4786-83cf-a5d43c7cb6f3
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# 数据类型说明符和等效项
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本书通常使用下表中所列的类型说明符的形式而不使用长形式，并且本书假设 `char` 类型在默认情况下有符号。  因此，在本书中，`char` 与 **signed char** 等效。  
  
### 类型说明符和等效项  
  
|类型说明符|等效项|  
|-----------|---------|  
|**signed char**1|`char`|  
|**signed int**|**signed**、`int`|  
|**signed short int**|**short**、`signed short`|  
|**signed long int**|**long**、**signed long**|  
|`unsigned char`|—|  
|`unsigned int`|`unsigned`|  
|**unsigned short int**|**unsigned short**|  
|**unsigned long int**|`unsigned long`|  
|**float**|—|  
|`long double`2|—|  
  
 1   当在默认情况下将 `char` 类型设为无符号时（通过指定 \/J 编译器选项），无法将 **signed char** 缩写为 `char`。  
  
 2   在 32 位操作系统中，Microsoft C 编译器将 **long double**  映射到类型 **double**。  
  
 **Microsoft 专用**  
  
 可以指定 \/J 编译器选项来将默认 `char` 类型从有符号更改为无符号。  当此选项生效时，`char` 与 `unsigned char` 的意义相同，您必须使用 **signed** 关键字来声明有符号字符值。  如果将 `char` 值显式声明为有符号，则 \/J 选项不会影响它，并且当其类型扩展为 `int` 类型时，该值将进行符号扩展。  当扩展到 `int` 类型时，`char` 类型为零扩展。  
  
 **结束 Microsoft 专用**  
  
## 请参阅  
 [C 类型说明符](../c-language/c-type-specifiers.md)