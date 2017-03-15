---
title: "offsetof 宏 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
apitype: "DLLExport"
f1_keywords: 
  - "offsetof"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "offsetof 宏"
  - "结构成员, 偏移量"
ms.assetid: f3b4eb16-a882-4d38-afc9-eebd976a7352
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# offsetof 宏
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

检索成员与其父结构的开头之间的偏移量。  
  
## 语法  
  
```  
  
        size_t offsetof(  
   structName,  
   memberName   
);  
```  
  
#### 参数  
 *structName*  
 父数据结构的名称。  
  
 `memberName`  
 确定其偏移量的父数据结构中成员的名称。  
  
## 返回值  
 `offsetof` 返回指定成员与其父数据结构的开头之间的偏移量（以字节为单位）。  它对于位域是未定义的。  
  
## 备注  
 `offsetof` 宏返回 `memberName` 与由 *structName* 指定的作为类型 `size_t` 的值的结构的开头之间的偏移量（以字节为单位）。  您可使用 `struct` 关键字指定类型。  
  
> [!NOTE]
>  `offsetof` 不是函数，无法使用 C 原型描述它。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`offsetof`|\<stddef.h\>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 库  
 [C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## 请参阅  
 [内存分配](../../c-runtime-library/memory-allocation.md)