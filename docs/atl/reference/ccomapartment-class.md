---
title: "CComApartment Class | Microsoft Docs"
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
  - "ATL::CComApartment"
  - "CComApartment"
  - "ATL.CComApartment"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "apartments in ATL EXE modules"
  - "CComApartment class"
ms.assetid: dbc177d7-7ee4-45f2-b563-d578a467ca93
caps.latest.revision: 20
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CComApartment Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类提供用于管理在一个线程池的EXE模块的一个单元支持。  
  
> [!IMPORTANT]
>  此选件类及其成员不能在Windows运行时执行的应用程序。  
  
## 语法  
  
```  
  
class CComApartment  
  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CComApartment::CComApartment](../Topic/CComApartment::CComApartment.md)|构造函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CComApartment::Apartment](../Topic/CComApartment::Apartment.md)|标记线程的起始地址。|  
|[CComApartment::GetLockCount](../Topic/CComApartment::GetLockCount.md)|返回线程的当前锁计数。|  
|[CComApartment::Lock](../Topic/CComApartment::Lock.md)|增加线程的锁计数。|  
|[CComApartment::Unlock](../Topic/CComApartment::Unlock.md)|递减线程的锁计数。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CComApartment::m\_dwThreadID](../Topic/CComApartment::m_dwThreadID.md)|包含的线程的标识符。|  
|[CComApartment::m\_hThread](../Topic/CComApartment::m_hThread.md)|包含线程的句柄。|  
|[CComApartment::m\_nLockCnt](../Topic/CComApartment::m_nLockCnt.md)|包含线程的当前锁计数。|  
  
## 备注  
 [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md) 用于`CComApartment` 管理在一个线程池的EXE模块的一个单元。  `CComApartment` 为递增和递减锁计数的方法在线程。  
  
## 要求  
 **Header:** atlbase.h  
  
## 请参阅  
 [Class Overview](../../atl/atl-class-overview.md)