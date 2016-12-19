---
title: "IThreadPoolConfig Interface | Microsoft Docs"
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
  - "IThreadPoolConfig"
  - "ATL::IThreadPoolConfig"
  - "ATL.IThreadPoolConfig"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IThreadPoolConfig interface"
ms.assetid: 69e642bf-6925-46e6-9a37-cce52231b1cc
caps.latest.revision: 24
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IThreadPoolConfig Interface
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此接口用于配置线程池的方法。  
  
> [!IMPORTANT]
>  此选件类及其成员不能在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]执行的应用程序。  
  
## 语法  
  
```  
  
      __interface  
__declspec(uuid("B1F64757-6E88-4fa2-8886-7848B0D7E660"))  
IThreadPoolConfig :  
public IUnknown  
```  
  
## 成员  
  
### 方法  
  
|||  
|-|-|  
|[GetSize](../Topic/IThreadPoolConfig::GetSize.md)|调用此方法获取线程数。该池的。|  
|[GetTimeout](../Topic/IThreadPoolConfig::GetTimeout.md)|在毫秒调用此方法以获得最大时间线程池将等待线程关闭。|  
|[SetSize](../Topic/IThreadPoolConfig::SetSize.md)|调用此方法设置线程数。该池的。|  
|[SetTimeout](../Topic/IThreadPoolConfig::SetTimeout.md)|在毫秒调用此方法设置最长时间线程池将等待线程关闭。|  
  
## 备注  
 此接口由 [CThreadPool](../../atl/reference/cthreadpool-class.md)实现。  
  
## 要求  
 **Header:** atlutil.h  
  
## 请参阅  
 [类](../../atl/reference/atl-classes.md)   
 [CThreadPool Class](../../atl/reference/cthreadpool-class.md)