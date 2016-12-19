---
title: "CComDynamicUnkArray Class | Microsoft Docs"
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
  - "ATL.CComDynamicUnkArray"
  - "CComDynamicUnkArray"
  - "ATL::CComDynamicUnkArray"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComDynamicUnkArray class"
  - "连接点 [C++], 管理"
ms.assetid: 202470d7-9a1b-498f-b96d-659d681acd65
caps.latest.revision: 17
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CComDynamicUnkArray Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类存储数组 **IUnknown** 指针。  
  
## 语法  
  
```  
class CComDynamicUnkArray  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|描述|  
|--------|--------|  
|[CComDynamicUnkArray::CComDynamicUnkArray](../Topic/CComDynamicUnkArray::CComDynamicUnkArray.md)|构造函数。  初始化集合值设置为 **NULL**，并且集合大小为零。|  
|[CComDynamicUnkArray::~CComDynamicUnkArray](../Topic/CComDynamicUnkArray::~CComDynamicUnkArray.md)|该析构函数。|  
  
### 公共方法  
  
|名称|描述|  
|--------|--------|  
|[CComDynamicUnkArray::Add](../Topic/CComDynamicUnkArray::Add.md)|调用此方法将 `IUnknown` 指向数组。|  
|[CComDynamicUnkArray::begin](../Topic/CComDynamicUnkArray::begin.md)|返回指向集合中的第一 `IUnknown` 指针。|  
|[CComDynamicUnkArray::clear](../Topic/CComDynamicUnkArray::clear.md)|空数组。|  
|[CComDynamicUnkArray::end](../Topic/CComDynamicUnkArray::end.md)|返回指向传递一个集合中的最后一 **IUnknown** 指针。|  
|[CComDynamicUnkArray::GetAt](../Topic/CComDynamicUnkArray::GetAt.md)|检索指定索引处的元素。|  
|[CComDynamicUnkArray::GetCookie](../Topic/CComDynamicUnkArray::GetCookie.md)|调用此方法获取cookie与特定 **IUnknown** 指针。|  
|[CComDynamicUnkArray::GetSize](../Topic/CComDynamicUnkArray::GetSize.md)|返回数组的长度。|  
|[CComDynamicUnkArray::GetUnknown](../Topic/CComDynamicUnkArray::GetUnknown.md)|调用此方法获取 **IUnknown** 指针与特定cookie。|  
|[CComDynamicUnkArray::Remove](../Topic/CComDynamicUnkArray::Remove.md)|调用此方法从数组中移除 **IUnknown** 指针。|  
  
## 备注  
 **CComDynamicUnkArray** 保存动态分配的一些 **IUnknown** 指针，因此每个中的一个接口的连接点。  **CComDynamicUnkArray** 可用作指向 [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md) 模板选件类的一个参数。  
  
 **CComDynamicUnkArray** 方法 [启动](../Topic/CComDynamicUnkArray::begin.md) 和 [结束](../Topic/CComDynamicUnkArray::end.md) 可用于通过所有循环连接点\(例如，时，都会激发事件时\)。  
  
 请参见 [Adding Connection Points to an Object](../../atl/adding-connection-points-to-an-object.md) 有关自动创建的详细信息连接点代理。  
  
> [!NOTE]
>  选件类 **CComDynamicUnkArrayAdd Class** 向导使用**Note**，当创建具有的控件\)时连接点。  如果您希望指定数量的手动联接，从 **CComDynamicUnkArray** 更改对 `CComUnkArray<`*n* `>`，其中 *n* 是的数字连接点必需。  
  
## 要求  
 **Header:** atlcom.h  
  
## 请参阅  
 [CComUnkArray Class](../../atl/reference/ccomunkarray-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)