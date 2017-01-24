---
title: "错误处理 (CRT) | Microsoft Docs"
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
  - "c.errors"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "错误处理, C 例程"
  - "错误处理, 库例程"
  - "逻辑错误"
  - "测试, 用于程序错误"
ms.assetid: 125ac697-9eb0-4152-a440-b7842f23d97f
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 错误处理 (CRT)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用这些例程处理程序错误。  
  
### 错误处理例程  
  
|例程|使用|.NET Framework 等效项|  
|--------|--------|------------------------|  
|[assert](../c-runtime-library/reference/assert-macro-assert-wassert.md)宏|编程的逻辑错误测试；中提供版本和调试运行库的版本|[\<caps:sentence id\="tgt8" sentenceid\="14fd9bf776829d73028df00162f7533f" class\="tgtSentence"\>System::Diagnostics::Debug::Assert\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.diagnostics.debug.assert.aspx)|  
|[\_ASSERT, \_ASSERTE](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) 宏|与`assert`类似，但是只在运行库的调试版本中可用|[\<caps:sentence id\="tgt11" sentenceid\="14fd9bf776829d73028df00162f7533f" class\="tgtSentence"\>System::Diagnostics::Debug::Assert\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.diagnostics.debug.assert.aspx)|  
|[clearerr](../c-runtime-library/reference/clearerr.md)|重置错误指示器。  调用 `rewind` 或在流还错误指示器。|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_eof](../c-runtime-library/reference/eof.md)|检查文件的结尾。底层 I\/O|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[feof](../c-runtime-library/reference/feof.md)|测试文件结尾  文件尾，`_read` 也指示当返回 0。|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[ferror](../c-runtime-library/reference/ferror.md)|测试流 I\/O 错误|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_RPT, \_RPTF](../c-runtime-library/reference/rpt-rptf-rptw-rptfw-macros.md) macros宏|生成报告类似于 `printf`，但是，只在运行库的调试版本|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_set\_error\_mode](../c-runtime-library/reference/set-error-mode.md)|修改 `__error_mode` 来确定C 运行时写可能关闭程序的错误的错误消息的非默认的位置。||  
|[\_set\_purecall\_handler](../c-runtime-library/reference/get-purecall-handler-set-purecall-handler.md)|设置一个纯虚函数调用的处理程序。||  
  
## 请参阅  
 [按类别分的运行时例程](../c-runtime-library/run-time-routines-by-category.md)