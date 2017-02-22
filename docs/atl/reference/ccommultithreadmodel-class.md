---
title: "CComMultiThreadModel Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CComMultiThreadModel"
  - "ATL.CComMultiThreadModel"
  - "ATL::CComMultiThreadModel"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL, 多线程处理"
  - "CComMultiThreadModel class"
  - "线程处理 [ATL]"
ms.assetid: db8f1662-2f7a-44b3-b341-ffbfb6e422a3
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CComMultiThreadModel Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CComMultiThreadModel` 为递增和递减变量的值提供线程安全的方法。  
  
## 语法  
  
```  
  
class CComMultiThreadModel  
  
```  
  
## 成员  
  
### 公共 Typedefs  
  
|名称|说明|  
|--------|--------|  
|[CComMultiThreadModel::AutoCriticalSection](../Topic/CComMultiThreadModel::AutoCriticalSection.md)|引用选件类 [CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md)。|  
|[CComMultiThreadModel::CriticalSection](../Topic/CComMultiThreadModel::CriticalSection.md)|引用选件类 [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)。|  
|[CComMultiThreadModel::ThreadModelNoCS](../Topic/CComMultiThreadModel::ThreadModelNoCS.md)|引用选件类 [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CComMultiThreadModel::Decrement](../Topic/CComMultiThreadModel::Decrement.md)|（静态）递减指定变量的值以线程安全的方式。|  
|[CComMultiThreadModel::Increment](../Topic/CComMultiThreadModel::Increment.md)|（静态）添加指定的变量的值以线程安全的方式。|  
  
## 备注  
 通常，通过两个 `typedef` 名称之一使用 `CComMultiThreadModel`，[CComObjectThreadModel](../Topic/CComObjectThreadModel.md) 或 [CComGlobalsThreadModel](../Topic/CComGlobalsThreadModel.md)。  每 `typedef` 引用的选件类依赖于线程模型使用，如下表所示:  
  
|typedef|单个线程|单元线程处理|自由线程处理|  
|-------------|----------|------------|------------|  
|`CComObjectThreadModel`|S|S|M|  
|`CComGlobalsThreadModel`|S|M|M|  
  
 S\=`CComSingleThreadModel`;M\=`CComMultiThreadModel`  
  
 `CComMultiThreadModel` 定义了三个 `typedef` 名称。  `AutoCriticalSection` 和 `CriticalSection` 引用来获取和释放临界区的所有权提供方法的选件类。  `ThreadModelNoCS` 引用选件类 [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)。  
  
## 要求  
 **Header:** atlbase.h  
  
## 请参阅  
 [CComSingleThreadModel Class](../../atl/reference/ccomsinglethreadmodel-class.md)   
 [CComAutoCriticalSection Class](../../atl/reference/ccomautocriticalsection-class.md)   
 [CComCriticalSection Class](../../atl/reference/ccomcriticalsection-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)