---
title: "CComSingleThreadModel Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.CComSingleThreadModel"
  - "CComSingleThreadModel"
  - "ATL::CComSingleThreadModel"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComSingleThreadModel class"
  - "single-threaded applications"
  - "single-threaded applications, ATL"
ms.assetid: e5dc30c7-405a-4ba4-8ae9-51937243fce8
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# CComSingleThreadModel Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类为递增和递减变量的值的方法。  
  
## 语法  
  
```  
  
class CComSingleThreadModel  
  
```  
  
## 成员  
  
### 公共 Typedefs  
  
|名称|说明|  
|--------|--------|  
|[CComSingleThreadModel::AutoCriticalSection](../Topic/CComSingleThreadModel::AutoCriticalSection.md)|引用选件类 [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)。|  
|[CComSingleThreadModel::CriticalSection](../Topic/CComSingleThreadModel::CriticalSection.md)|引用选件类 `CComFakeCriticalSection`。|  
|[CComSingleThreadModel::ThreadModelNoCS](../Topic/CComSingleThreadModel::ThreadModelNoCS.md)|引用 `CComSingleThreadModel`。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CComSingleThreadModel::Decrement](../Topic/CComSingleThreadModel::Decrement.md)|递减所指定的变量的值。  此实现不是线程安全的。|  
|[CComSingleThreadModel::Increment](../Topic/CComSingleThreadModel::Increment.md)|递增指定变量的值。  此实现不是线程安全的。|  
  
## 备注  
 `CComSingleThreadModel` 为递增和递减变量的值的方法。  不同 [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) 和 [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)，这些方法不是线程安全的。  
  
 通常，通过两个 `typedef` 名称之一使用 `CComSingleThreadModel`，[CComObjectThreadModel](../Topic/CComObjectThreadModel.md) 或 [CComGlobalsThreadModel](../Topic/CComGlobalsThreadModel.md)。  每 `typedef` 引用的选件类依赖于线程模型使用，如下表所示:  
  
|typedef|单个线程模型|单元\(sta\)线程处理模型|自由线程模型|  
|-------------|------------|---------------------|------------|  
|`CComObjectThreadModel`|S|S|M|  
|`CComGlobalsThreadModel`|S|M|M|  
  
 S\=`CComSingleThreadModel`;M\=`CComMultiThreadModel`  
  
 `CComSingleThreadModel` 定义了三个 `typedef` 名称。  `ThreadModelNoCS` 引用 `CComSingleThreadModel`。  `AutoCriticalSection` 和 `CriticalSection` 引用选件类 [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)，提供空方法与获取和释放临界区的所有权。  
  
## 要求  
 **Header:** atlbase.h  
  
## 请参阅  
 [Class Overview](../../atl/atl-class-overview.md)