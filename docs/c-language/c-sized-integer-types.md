---
title: "C 调整了大小的整型 | Microsoft Docs"
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
  - "调整了大小的整型"
ms.assetid: 0d6199b4-d0ab-4e8c-a769-785f5afb92eb
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C 调整了大小的整型
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 Microsoft C 支持固定大小整数类型。  可以使用 \_\_int*n* 类型说明符声明 8 位、16 位、32 位或 64 位整数变量，其中 *n* 是整数变量的大小（以位为单位）。  *n* 的值可以是 8、16、32 或 64。  以下示例为四种类型的固定大小整数各声明了一个变量：  
  
```  
__int8 nSmall;      // Declares 8-bit integer  
__int16 nMedium;    // Declares 16-bit integer  
__int32 nLarge;     // Declares 32-bit integer  
__int64 nHuge;      // Declares 64-bit integer  
```  
  
 固定大小整数的前三种类型是大小相同的 ANSI 类型的同义词，用于编写在多个平台中具有相同的行为的可移植代码。  请注意，\_\_int8 数据类型与 char 类型是同义词，\_\_int16 与 short 类型是同义词，\_\_int32 与 int 类型是同义词。  \_\_int64 类型没有等效的 ANSI 匹配项。  
  
 **结束 Microsoft 专用**  
  
## 请参阅  
 [基本类型的存储](../c-language/storage-of-basic-types.md)