---
title: "__dllonexit | Microsoft Docs"
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
  - "__dllonexit"
apilocation: 
  - "msvcrt.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr100.dll"
  - "msvcr80.dll"
  - "msvcr120.dll"
  - "msvcr90.dll"
  - "msvcr120_clr0400.dll"
apitype: "DLLExport"
f1_keywords: 
  - "__dllonexit"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__dllonexit"
ms.assetid: 708f2ceb-f95c-46b0-a58d-d68b3fa36f12
caps.latest.revision: 4
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __dllonexit
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在退出时间注册一个实例被调用。  
  
## 语法  
  
```  
_onexit_t __dllonexit(  
   _onexit_t func,  
   _PVFV **  pbegin,   
   _PVFV **  pend   
   )  
```  
  
#### 参数  
 `func`  
 退出时指向一个要执行的函数的指针。  
  
 `pbegin`  
 在分离时，指向一个指向函数列表开头的变量的指针。  
  
 `pend`  
 在分离时，指向一个指向函数列表结尾的变量的指针。  
  
## 返回值  
 如果成功，则指针指向用户函数。  否则，空指针。  
  
## 备注  
 `__dllonexit` 函数类似于 [\_onexit](../c-runtime-library/reference/onexit-onexit-m.md) 函数，除了通过函数对此例程不可见而使用全局变量。  此函数使用 `pbegin` 和 `pend` 参数，而不是全局变量。  
  
 `_onexit` 和 `atexit` 函数在 DLL 连接 MSVCRT.LIB 必须维护它们的 atexit\/\_onexit 列表。  该例程是通过此 DLLs 调用的员工。  
  
 `_PVFV` 类型正如 `typedef void (__cdecl *_PVFV)(void)` 所定义的。  
  
## 要求  
  
|例程|必需文件|  
|--------|----------|  
|\_\_dllonexit|onexit.c|  
  
## 请参阅  
 [\_onexit、\_onexit\_m](../c-runtime-library/reference/onexit-onexit-m.md)