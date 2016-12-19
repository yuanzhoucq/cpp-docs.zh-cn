---
title: "IWorkerThreadClient Interface | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.IWorkerThreadClient"
  - "ATL::IWorkerThreadClient"
  - "IWorkerThreadClient"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IWorkerThreadClient interface"
ms.assetid: 56f4a2f5-007e-4a33-9e20-05187629f715
caps.latest.revision: 24
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IWorkerThreadClient Interface
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`IWorkerThreadClient` 是 [CWorkerThread](../../atl/reference/cworkerthread-class.md) 选件类的客户端实现的接口。  
  
> [!IMPORTANT]
>  此选件类及其成员不能在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]执行的应用程序。  
  
## 语法  
  
```  
  
__interface IWorkerThreadClient  
  
```  
  
## 成员  
  
### 方法  
  
|||  
|-|-|  
|[CloseHandle](../Topic/IWorkerThreadClient::CloseHandle.md)|实现此方法关闭处理与此对象关联的。|  
|[执行](../Topic/IWorkerThreadClient::Execute.md)|当处理与此对象关联的变为终止状态时，实现此方法执行代码。|  
  
## 备注  
 实现此接口，则在辅助线程需要执行的用于响应变为的句柄信号的代码时。  
  
## 要求  
 **Header:** atlutil.h  
  
## 请参阅  
 [类](../../atl/reference/atl-classes.md)   
 [CWorkerThread Class](../../atl/reference/cworkerthread-class.md)