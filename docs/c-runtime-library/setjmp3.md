---
title: "_setjmp3 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_setjmp3"
apilocation: 
  - "msvcrt.dll"
  - "msvcr90.dll"
  - "msvcr110.dll"
  - "msvcr80.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr100.dll"
  - "msvcr120.dll"
apitype: "DLLExport"
f1_keywords: 
  - "setjmp3"
  - "_setjmp3"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_setjmp3 函数"
  - "setjmp3 函数"
ms.assetid: 6129c2f3-8bac-4fdb-a827-44e1eebba500
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# _setjmp3
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

内部 CRT 函数。  `setjmp` 函数的新实现。  
  
## 语法  
  
```  
int _setjmp3(    OUT jmp_buf env,    int count,    (optional parameters) );  
```  
  
#### 参数  
 \[out\] `env`  
 用于存储状态信息的缓冲区地址。  
  
 \[in\] `count`  
 存储在 `optional parameters` 中的信息的附加 `DWORD` 数。  
  
 \[in\] `optional parameters`  
 由 `setjmp` 内部函数向下推送的其他数据。  第一个 `DWORD` 是一个用于展开多余数据并返回到永久性注册状态的函数指针。  第二个 `DWORD` 是要还原的尝试级别。  之后的所有数据都将保存在 `jmp_buf` 的通用数据数组中。  
  
## 返回值  
 始终返回 0。  
  
## 备注  
 请不要在 C\+\+ 程序中使用此函数。  它是一个不支持 C\+\+ 的内部函数。  有关如何使用 `setjmp`的更多信息，请参见[使用 setjmp\/longjmp](../cpp/using-setjmp-longjmp.md)。  
  
## 要求  
  
## 请参阅  
 [按字母顺序的函数参考](../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [setjmp](../c-runtime-library/reference/setjmp.md)