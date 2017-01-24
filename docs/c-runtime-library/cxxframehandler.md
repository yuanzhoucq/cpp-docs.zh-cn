---
title: "__CxxFrameHandler | Microsoft Docs"
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
  - "__CxxFrameHandler"
apilocation: 
  - "msvcr110.dll"
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr100.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr90.dll"
  - "msvcr120.dll"
apitype: "DLLExport"
f1_keywords: 
  - "__CxxFrameHandler"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__CxxFrameHandler"
ms.assetid: b79ac97f-425a-42ae-9b91-8beaef935333
caps.latest.revision: 3
caps.handback.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __CxxFrameHandler
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

内部 CRT 函数。  由 CRT 用于处理结构化异常帧。  
  
## 语法  
  
```cpp  
EXCEPTION_DISPOSITION __CxxFrameHandler(       EHExceptionRecord  *pExcept,       EHRegistrationNode *pRN,       void               *pContext,        DispatcherContext  *pDC    )  
```  
  
#### 参数  
 `pExcept`  
 传递给可能的 `catch` 语句的异常记录。  
  
 `pRN`  
 有关用于处理异常的堆栈帧的动态信息。  有关详细信息，请参阅 ehdata.h。  
  
 `pContext`  
 上下文。  （不可用于 Intel 处理器上。）  
  
 `pDC`  
 有关函数入口和堆栈帧的其他信息。  
  
## 返回值  
 由 [try\-except 语句](../cpp/try-except-statement.md) 使用的 *filter expression* 值之一。  
  
## 备注  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|\_\_CxxFrameHandler|excpt.h，ehdata.h|