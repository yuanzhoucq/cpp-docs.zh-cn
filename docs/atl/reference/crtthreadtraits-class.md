---
title: "CRTThreadTraits Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL::CRTThreadTraits"
  - "ATL.CRTThreadTraits"
  - "CRTThreadTraits"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CRTThreadTraits class"
  - "线程处理 [ATL], creation functions"
  - "线程处理 [ATL], CRT threads"
ms.assetid: eb6e20b0-c2aa-4170-8e34-aaeeacc86343
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CRTThreadTraits Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类。CRT线程提供创建功能。  如果线程将使用CRT函数，请使用此选件类。  
  
> [!IMPORTANT]
>  此选件类及其成员不能在Windows运行时执行的应用程序。  
  
## 语法  
  
```  
  
class CRTThreadTraits  
  
```  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CRTThreadTraits::CreateThread](../Topic/CRTThreadTraits::CreateThread.md)|（静态）调用此函数创建能够使用CRT函数的线程。|  
  
## 备注  
 线程特征是为线程的特定类型提供创建功能的选件类。  创建函数的签名和语义和Windows [CreateThread](http://msdn.microsoft.com/library/windows/desktop/ms682453) 功能相同。  
  
 下面选件类使用线程特征:  
  
-   [CThreadPool](../../atl/reference/cthreadpool-class.md)  
  
-   [CWorkerThread](../../atl/reference/cworkerthread-class.md)  
  
 如果线程不使用CRT函数，请使用 [Win32ThreadTraits](../../atl/reference/win32threadtraits-class.md)。  
  
## 要求  
 **Header:** atlbase.h  
  
## 请参阅  
 [Class Overview](../../atl/atl-class-overview.md)