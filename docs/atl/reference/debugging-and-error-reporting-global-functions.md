---
title: "Debugging and Error Reporting Global Functions | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "函数 [ATL], 错误报告"
ms.assetid: 11339c02-98cd-428d-b3b9-7deeb155a6a3
caps.latest.revision: 17
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Debugging and Error Reporting Global Functions
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

这些功能提供有用的调试和跟踪功能。  
  
|||  
|-|-|  
|[AtlHresultFromLastError](../Topic/AtlHresultFromLastError.md)|以HRESULT的形式，则返回 `GetLastError` 错误代码。|  
|[AtlHresultFromWin32](../Topic/AtlHresultFromWin32.md)|将Win32错误代码转换为HRESULT。|  
|[AtlReportError](../Topic/AtlReportError.md)|设置 **IErrorInfo** 提供错误详细信息到客户端。|  
|[AtlThrow](../Topic/AtlThrow.md)|引发 `CAtlException`。|  
|[AtlThrowLastWin32](../Topic/AtlThrowLastWin32.md)|调用此函数发出信号错误基于Windows功能 `GetLastError`的结果。|  
|[AtlTraceLoadSettings](../../misc/atltraceloadsettings.md)|调用此函数从文件加载跟踪设置。|  
|[AtlTraceSaveSettings](../../misc/atltracesavesettings.md)|调用此函数保存当前跟踪设置为文件。|  
  
## 请参阅  
 [函数](../../atl/reference/atl-functions.md)   
 [Debugging and Error Reporting Macros](../../atl/reference/debugging-and-error-reporting-macros.md)