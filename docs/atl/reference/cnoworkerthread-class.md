---
title: "CNoWorkerThread Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL::CNoWorkerThread"
  - "ATL.CNoWorkerThread"
  - "CNoWorkerThread"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CNoWorkerThread class"
ms.assetid: 29f06bae-b658-4aac-9c14-331e996d25d1
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CNoWorkerThread Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

如果想要禁用动态缓存维护，请使用此选件类作为参数。`MonitorClass` 模板参数传递到缓存选件类。  
  
> [!IMPORTANT]
>  此选件类及其成员不能在Windows运行时执行的应用程序。  
  
## 语法  
  
```  
  
class CNoWorkerThread  
  
```  
  
## 成员  
  
### 公共方法  
  
|名称|描述|  
|--------|--------|  
|[CNoWorkerThread::AddHandle](../Topic/CNoWorkerThread::AddHandle.md)|[CWorkerThread::AddHandle](../Topic/CWorkerThread::AddHandle.md)不运行等效。|  
|[CNoWorkerThread::AddTimer](../Topic/CNoWorkerThread::AddTimer.md)|[CWorkerThread::AddTimer](../Topic/CWorkerThread::AddTimer.md)不运行等效。|  
|[CNoWorkerThread::GetThreadHandle](../Topic/CNoWorkerThread::GetThreadHandle.md)|[CWorkerThread::GetThreadHandle](../Topic/CWorkerThread::GetThreadHandle.md)不运行等效。|  
|[CNoWorkerThread::GetThreadId](../Topic/CNoWorkerThread::GetThreadId.md)|[CWorkerThread::GetThreadId](../Topic/CWorkerThread::GetThreadId.md)不运行等效。|  
|[CNoWorkerThread::Initialize](../Topic/CNoWorkerThread::Initialize.md)|[CWorkerThread::Initialize](../Topic/CWorkerThread::Initialize.md)不运行等效。|  
|[CNoWorkerThread::RemoveHandle](../Topic/CNoWorkerThread::RemoveHandle.md)|[CWorkerThread::RemoveHandle](../Topic/CWorkerThread::RemoveHandle.md)不运行等效。|  
|[CNoWorkerThread::Shutdown](../Topic/CNoWorkerThread::Shutdown.md)|[CWorkerThread::Shutdown](../Topic/CWorkerThread::Shutdown.md)不运行等效。|  
  
## 备注  
 此选件类提供公共接口和 [CWorkerThread](../../atl/reference/cworkerthread-class.md)相同。  此接口应由 `MonitorClass` 模板参数提供给缓存选件类。  
  
 本选件类的方法没有执行。  返回HRESULT的方法始终返回S\_OK，并且，将处理返回或线程ID的方法始终返回0。  
  
## 要求  
 **Header:** atlutil.h