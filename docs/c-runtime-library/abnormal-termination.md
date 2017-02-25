---
title: "_abnormal_termination | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_abnormal_termination"
apilocation: 
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr90.dll"
  - "msvcr120.dll"
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr100.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_abnormal_termination"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_abnormal_termination"
ms.assetid: 952970a4-9586-4c3d-807a-db729448c91c
caps.latest.revision: 2
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 2
---
# _abnormal_termination
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

说明 [尝试最终语句](../cpp/try-finally-statement.md) 的 `__finally` 块是否输入，当系统停止执行处理程序的内部列表时。  
  
## 语法  
  
```cpp  
int   _abnormal_termination(  
   );  
```  
  
## 返回值  
 如果系统 *展开* 堆栈， `true`；否则， `false`。  
  
## 备注  
 这是用来管理展开异常的一个内部函数，并且不应从用户代码调用。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|\_abnormal\_termination|excpt.h|  
  
## 请参阅  
 [try\-finally 语句](../cpp/try-finally-statement.md)