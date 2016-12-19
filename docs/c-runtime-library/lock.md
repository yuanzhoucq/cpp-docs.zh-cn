---
title: "_lock | Microsoft Docs"
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
  - "_lock"
apilocation: 
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr100.dll"
  - "msvcr90.dll"
  - "msvcr80.dll"
  - "msvcr110.dll"
  - "msvcrt.dll"
  - "msvcr120_clr0400.dll"
apitype: "DLLExport"
f1_keywords: 
  - "lock"
  - "_lock"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "lock 函数"
  - "_lock 函数"
ms.assetid: 29f77c37-30de-4b3d-91b6-030216e645a6
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _lock
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

获取多线程锁定。  
  
> [!IMPORTANT]
>  此函数已过时。 从 Visual Studio 2015 开始，CRT 中不再提供此函数。  
  
## 语法  
  
```  
void __cdecl _lock  
   int locknum  
);  
```  
  
#### 参数  
 \[in\] `locknum`  
 要获取的锁定标识符。  
  
## 备注  
 如果已获取锁定，则此方法仍获取锁定会导致内部 C 运行时 \(CRT\) 错误。 如果此方法无法获取锁定，则它将退出并显示错误，同时将错误代码设置为 `_RT_LOCK`。  
  
## 要求  
 **源：**mlock.c  
  
## 请参阅  
 [按字母顺序的函数参考](../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [\_unlock](../c-runtime-library/unlock.md)