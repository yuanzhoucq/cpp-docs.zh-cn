---
title: "__pctype_func | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "__pctype_func"
apilocation: 
  - "msvcrt.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr120.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr80.dll"
apitype: "DLLExport"
f1_keywords: 
  - "__pctype_func"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__pctype_func"
ms.assetid: d52b8add-d07d-4516-a22f-e836cde0c57f
caps.latest.revision: 2
caps.handback.revision: 2
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __pctype_func
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

检索指向字符分类的信息。  
  
## 语法  
  
```cpp  
const unsigned short *__pctype_func(  
   )  
```  
  
## 返回值  
 检索指向字符分类的信息。  
  
## 备注  
 在字符类表仅供内部使用类和类型字符 `char`的各个函数使用信息。  有关更多信息，请参见[\_pctype、\_pwctype、\_wctype、\_mbctype、\_mbcasemap](../c-runtime-library/pctype-pwctype-wctype-mbctype-mbcasemap.md) 的`Remarks`一节。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|\_\_pctype\_func|ctype.h|  
  
## 请参阅  
 [\_pctype、\_pwctype、\_wctype、\_mbctype、\_mbcasemap](../c-runtime-library/pctype-pwctype-wctype-mbctype-mbcasemap.md)