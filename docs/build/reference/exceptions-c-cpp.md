---
title: "异常 (C/C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ERROR_MOD_NOT_FOUND"
  - "vcppException"
  - "ERROR_SEVERITY_ERROR"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C++ 异常处理, DLL 的延迟加载"
  - "DLL 的延迟加载, 异常"
  - "ERROR_MOD_NOT_FOUND 异常"
  - "ERROR_SEVERITY_ERROR 异常"
  - "vcppException"
ms.assetid: c03be05d-1c39-4f35-84cf-00c9af3bae9a
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 异常 (C/C++)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

遇到失败时可引发两个异常代码：  
  
-   **LoadLibrary** 失败的异常代码。  
  
-   **GetProcAddress** 失败的异常代码。  
  
 下面是异常信息：  
  
```  
//  
// Exception information  
//  
#define FACILITY_VISUALCPP  ((LONG)0x6d)  
#define VcppException(sev,err)  ((sev) | (FACILITY_VISUALCPP<<16) | err)  
```  
  
 引发的异常代码是标准 VcppException\(ERROR\_SEVERITY\_ERROR、ERROR\_MOD\_NOT\_FOUND\) 和 VcppException\(ERROR\_SEVERITY\_ERROR、ERROR\_PROC\_NOT\_FOUND\) 值。  异常在 LPDWORD 值中传递指向 **DelayLoadInfo** 结构的指针，该指针可由 [EXCEPTION\_RECORD](http://msdn.microsoft.com/library/windows/desktop/aa363082) 结构的 ExceptionInformation\[0\] 字段中的 **GetExceptionInformation** 检索到。  
  
 另外，如果在 grAttrs 字段中设置的位不正确，则引发异常 ERROR\_INVALID\_PARAMETER。  无论从哪方面看，该异常都是致命的。  
  
 有关更多信息，请参见[结构和常数定义](../../build/reference/structure-and-constant-definitions.md)。  
  
## 请参阅  
 [错误处理和通知](../../build/reference/error-handling-and-notification.md)