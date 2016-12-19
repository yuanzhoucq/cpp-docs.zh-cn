---
title: "异常处理例程 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.exceptions"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "异常处理, 例程"
ms.assetid: f60548c6-850a-4e1e-a79b-a2a6a541ab62
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 异常处理例程
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在程序执行时使用异常处理功能的 C\+\+ 从意外事件中恢复。  
  
### 异常处理函数  
  
|功能|使用|.NET Framework 等效项|  
|--------|--------|------------------------|  
|[\_set\_se\_translator](../c-runtime-library/reference/set-se-translator.md)|处理作为 C\+\+ 键入异常的 Win32 异常 \(C 结构化异常\) 。|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[set\_terminate](../c-runtime-library/reference/set-terminate-crt.md)|安装被`terminate` 调用的终端函数。|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[set\_unexpected](../c-runtime-library/reference/set-unexpected-crt.md)|安装你自己的通过 `unexpected` 被调用的终端函数。|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[terminate](../c-runtime-library/reference/terminate-crt.md)|在异常之后，在某些情况下自动调用。  `terminate` 函数调用使用指定的函数 `abort` 或 `set_terminate`|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[unexpected](../c-runtime-library/reference/unexpected-crt.md)|调用 `terminate` 或使用 `set_unexpected` 指定的函数。  当前的 Microsoft C\+\+异常处理实现不使用`unexpected` 函数。|[\<caps:sentence id\="tgt30" sentenceid\="ec8332f3bf55c7bd183338eca87744ec" class\="tgtSentence"\>System::Exception 类\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.exception.aspx)|  
  
## 请参阅  
 [按类别分的运行时例程](../c-runtime-library/run-time-routines-by-category.md)