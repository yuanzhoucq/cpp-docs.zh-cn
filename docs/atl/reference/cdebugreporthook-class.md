---
title: "CDebugReportHook Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.CDebugReportHook"
  - "CDebugReportHook"
  - "ATL::CDebugReportHook"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDebugReportHook class"
ms.assetid: 798076c3-6e63-4286-83b8-aa1bbcd0c20c
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# CDebugReportHook Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用此选件类发送调试报告为命名管道。  
  
## 语法  
  
```  
  
class CDebugReportHook  
  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CDebugReportHook::CDebugReportHook](../Topic/CDebugReportHook::CDebugReportHook.md)|调用 [SetPipeName](../Topic/CDebugReportHook::SetPipeName.md)、 [SetTimeout](../Topic/CDebugReportHook::SetTimeout.md)和 [SetHook](../Topic/CDebugReportHook::SetHook.md)。|  
|[CDebugReportHook::~CDebugReportHook](../Topic/CDebugReportHook::~CDebugReportHook.md)|调用 [CDebugReportHook::RemoveHook](../Topic/CDebugReportHook::RemoveHook.md)。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CDebugReportHook::CDebugReportHookProc](../Topic/CDebugReportHook::CDebugReportHookProc.md)|（静态）挂钩到C运行时的自定义报告函数调试报告进程。|  
|[CDebugReportHook::RemoveHook](../Topic/CDebugReportHook::RemoveHook.md)|调用此方法发送停止调试报告为命名管道和还原以前的报告挂钩。|  
|[CDebugReportHook::SetHook](../Topic/CDebugReportHook::SetHook.md)|调用此方法开始调试报告发送到命名管道。|  
|[CDebugReportHook::SetPipeName](../Topic/CDebugReportHook::SetPipeName.md)|调用此方法设置调试报告将发送管道的设备和名称。|  
|[CDebugReportHook::SetTimeout](../Topic/CDebugReportHook::SetTimeout.md)|在毫秒调用此方法设置时间此选件类将等待命名管道变得可用。|  
  
## 备注  
 创建此选件类实例来调试服务生成或应用程序发送调试报告为命名管道。  调试报告通过调用 [\_CrtDbgReport](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md) 或使用包装生成此功能\(如 [ATLTRACE](../Topic/ATLTRACE%20\(ATL\).md) 和 [ATLASSERT](../Topic/ATLASSERT.md) 宏。  
  
 允许您以交互方式调试组件运行在非交互式的 [窗口区域](http://msdn.microsoft.com/library/windows/desktop/ms687096)于此选件类的使用。  
  
 请注意使用线程的基础安全上下文，调试报告发送。  模拟暂时禁用，以便调试报表中查看在低权限的用户模拟发生的情况，例如Web应用程序。  
  
## 要求  
 **Header:** atlutil.h  
  
## 请参阅  
 [类](../../atl/reference/atl-classes.md)