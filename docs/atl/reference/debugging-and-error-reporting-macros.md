---
title: "Debugging and Error Reporting Macros | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "宏, 错误报告"
ms.assetid: 4da9b87f-ec5c-4a32-ab93-637780909b9d
caps.latest.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 19
---
# Debugging and Error Reporting Macros
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

这些宏提供有用的调试和跟踪功能。  
  
|||  
|-|-|  
|[\_ATL\_DEBUG\_INTERFACES](../Topic/_ATL_DEBUG_INTERFACES.md)|编写，"输出"窗口，检测的任何接口泄漏，当 `_Module.Term` 调用。|  
|[\_ATL\_DEBUG\_QI](../Topic/_ATL_DEBUG_QI.md)|编写对的所有调用 `QueryInterface` "输出"窗口。|  
|[ATLASSERT](../Topic/ATLASSERT.md)|执行与 [\_ASSERTE](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) 宏在C运行库中找到的功能。|  
|[ATLENSURE](../Topic/ATLENSURE.md)|执行参数验证。  如果需要调用 `AtlThrow`|  
|[ATLTRACENOTIMPL](../Topic/ATLTRACENOTIMPL.md)|将消息发送到转储计算机所指定的功能未实现。|  
|[ATLTRACE](../Topic/ATLTRACE%20\(ATL\).md)|警告到一个输出设备报告，如调试器窗口中，根据指定的标志和级别。  包括用于向后兼容。|  
|[ATLTRACE2](../Topic/ATLTRACE2.md)|警告到一个输出设备报告，如调试器窗口中，根据指定的标志和级别。|  
  
## 请参阅  
 [Macros](../../atl/reference/atl-macros.md)   
 [Debugging and Error Reporting Global Functions](../../atl/reference/debugging-and-error-reporting-global-functions.md)