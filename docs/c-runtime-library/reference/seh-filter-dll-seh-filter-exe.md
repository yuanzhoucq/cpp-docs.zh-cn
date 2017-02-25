---
title: "_seh_filter_dll, _seh_filter_exe | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_XcptFilter"
  - "_seh_filter_dll"
  - "_seh_filter_exe"
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
  - "api-ms-win-crt-runtime-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "XcptFilter"
  - "_XcptFilter"
  - "_seh_filter_dll"
  - "_seh_filter_exe"
  - "corecrt_startup/_seh_filter_exe"
  - "corecrt_startup/_seh_filter_dll"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "XcptFilter 函数"
  - "_XcptFilter 函数"
  - "_seh_filter_dll 函数"
  - "_seh_filter_exe 函数"
ms.assetid: 747e5963-3a12-4bf5-b5c4-d4c1b6068e15
caps.latest.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 14
---
# _seh_filter_dll, _seh_filter_exe
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

标识异常和要采取的相关操作。  
  
## 语法  
  
```  
int __cdecl _seh_filter_dll(  
   unsigned long _ExceptionNum,  
   struct _EXCEPTION_POINTERS* _ExceptionPtr  
);  
int __cdecl _seh_filter_exe(  
   unsigned long _ExceptionNum,  
   struct _EXCEPTION_POINTERS* _ExceptionPtr  
);  
```  
  
#### 参数  
 \[in\] `_ExceptionNum`  
 异常的标识符。  
  
 \[in\] `_ExceptionPtr`  
 指向异常信息的指针。  
  
## 返回值  
 用于依据异常处理的结果指示要采取的操作的整数。  
  
## 备注  
 这些方法由 [try\-except 语句](../../cpp/try-except-statement.md) 的异常筛选器表达式调用。 该方法查询固定的内部表来标识异常并确定适当的操作，如下所示。 异常编号在 winnt.h 中定义，信号编号在 signal.h 中定义。  
  
|异常编号 \(unsigned long\)|信号编号|  
|----------------------------|----------|  
|STATUS\_ACCESS\_VIOLATION|SIGSEGV|  
|STATUS\_ILLEGAL\_INSTRUCTION|SIGILL|  
|STATUS\_PRIVILEGED\_INSTRUCTION|SIGILL|  
|STATUS\_FLOAT\_DENORMAL\_OPERAND|SIGFPE|  
|STATUS\_FLOAT\_DIVIDE\_BY\_ZERO|SIGFPE|  
|STATUS\_FLOAT\_INEXACT\_RESULT|SIGFPE|  
|STATUS\_FLOAT\_INVALID\_OPERATION|SIGFPE|  
|STATUS\_FLOAT\_OVERFLOW|SIGFPE|  
|STATUS\_FLOAT\_STACK\_CHECK|SIGFPE|  
|STATUS\_FLOAT\_UNDERFLOW|SIGFPE|  
  
## 要求  
 **标头：**corecrt\_startup.h  
  
## 请参阅  
 [按字母顺序的函数参考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)