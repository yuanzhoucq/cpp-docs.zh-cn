---
title: "Win32ThreadTraits Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "Win32ThreadTraits"
  - "ATL::Win32ThreadTraits"
  - "ATL.Win32ThreadTraits"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "线程处理 [ATL], creation functions"
  - "线程处理 [ATL], Windows threads"
  - "Win32ThreadTraits class"
ms.assetid: 50279c38-eae1-4301-9ea6-97ccea580f3e
caps.latest.revision: 20
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Win32ThreadTraits Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类对于Windows线程提供创建功能。  如果线程不使用CRT函数，请使用此选件类。  
  
> [!IMPORTANT]
>  此选件类及其成员不能在Windows运行时执行的应用程序。  
  
## 语法  
  
```  
  
class Win32ThreadTraits  
  
```  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[Win32ThreadTraits::CreateThread](../Topic/Win32ThreadTraits::CreateThread.md)|（静态）调用此函数创建不应使用CRT函数的线程。|  
  
## 备注  
 线程特征是为线程的特定类型提供创建功能的选件类。  创建函数的签名和语义和Windows [CreateThread](http://msdn.microsoft.com/library/windows/desktop/ms682453) 功能相同。  
  
 下面选件类使用线程特征:  
  
-   [CThreadPool](../../atl/reference/cthreadpool-class.md)  
  
-   [CWorkerThread](../../atl/reference/cworkerthread-class.md)  
  
 如果线程使用CRT函数，请使用 [CRTThreadTraits](../../atl/reference/crtthreadtraits-class.md)。  
  
## 要求  
 **Header:** atlbase.h  
  
## 请参阅  
 [Class Overview](../../atl/atl-class-overview.md)