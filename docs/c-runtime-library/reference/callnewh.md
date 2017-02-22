---
title: "_callnewh | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_callnewh"
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
  - "api-ms-win-crt-heap-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_callnewh"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_callnewh"
ms.assetid: 4dcb73e9-6384-4d12-a973-a8807d4de7a8
caps.latest.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 3
---
# _callnewh
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

调用当前已安装的 *新的处理程序*。  
  
## 语法  
  
```cpp  
int _callnewh(  
   size_t size  
   )  
  
```  
  
#### 参数  
 `size`  
 给[新的运算符](../../cpp/new-operator-cpp.md) 尝试分配的内存量。  
  
## 返回值  
  
|值|描述|  
|-------|--------|  
|0|失败：未安装新的处理程序或没有激活新的处理程序。|  
|1|成功：安装并激活新的处理程序。  可以重试分配内存。|  
  
## 异常  
 如果不能定位到 *新的处理程序* ，则该函数抛出 [bad\_alloc](../../standard-library/bad-alloc-class.md) 。  
  
## 备注  
 如果 [新的操作数](../../cpp/new-operator-cpp.md) 未能成功分配内存，则调用 *新的处理程序* 。  新的处理程序可能随后启动某些相应的操作，例如释放内存以便后续分配成功。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|\_callnewh|internal.h|  
  
## 请参阅  
 [\_set\_new\_handler](../../c-runtime-library/reference/set-new-handler.md)   
 [\_set\_new\_mode](../../c-runtime-library/reference/set-new-mode.md)