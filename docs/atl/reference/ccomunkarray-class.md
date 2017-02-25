---
title: "CComUnkArray Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.CComUnkArray"
  - "ATL.CComUnkArray<nMaxSize>"
  - "ATL::CComUnkArray<nMaxSize>"
  - "ATL::CComUnkArray"
  - "CComUnkArray"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComUnkArray class"
  - "连接点 [C++], 管理"
ms.assetid: 5fd4b378-a7b5-4cc1-8866-8ab72a73639e
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 20
---
# CComUnkArray Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类存储 **IUnknown** 指针和旨在用作参数 [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md) 模板选件类。  
  
## 语法  
  
```  
template<  
   unsigned int nMaxSize  
>  
class CComUnkArray  
```  
  
#### 参数  
 *nMaxSize*  
 的 **IUnknown** 指针的最大数在静态数组可保存。  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CComUnkArray::CComUnkArray](../Topic/CComUnkArray::CComUnkArray.md)|构造函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CComUnkArray::Add](../Topic/CComUnkArray::Add.md)|调用此方法将 **IUnknown** 指向数组。|  
|[CComUnkArray::begin](../Topic/CComUnkArray::begin.md)|返回指向集合中的第一 **IUnknown** 指针。|  
|[CComUnkArray::end](../Topic/CComUnkArray::end.md)|返回指向传递一个集合中的最后一 **IUnknown** 指针。|  
|[CComUnkArray::GetCookie](../Topic/CComUnkArray::GetCookie.md)|调用此方法获取cookie与特定 **IUnknown** 指针。|  
|[CComUnkArray::GetUnknown](../Topic/CComUnkArray::GetUnknown.md)|调用此方法获取 **IUnknown** 指针与特定cookie。|  
|[CComUnkArray::Remove](../Topic/CComUnkArray::Remove.md)|调用此方法从数组中移除 **IUnknown** 指针。|  
  
## 备注  
 **CComUnkArray** 保存 **IUnknown** 指针的内置的数字，每中的一个接口的连接点。  **CComUnkArray** 可用作指向 [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md) 模板选件类的一个参数。  **CComUnkArray\<1\>** 是经过优化的连接点 **CComUnkArray** 的模板专用化。  
  
 **CComUnkArray** 方法 [启动](../Topic/CComUnkArray::begin.md) 和 [结束](../Topic/CComUnkArray::end.md) 可用于通过所有循环连接点\(例如，时，都会激发事件时）。  
  
 请参见 [Adding Connection Points to an Object](../../atl/adding-connection-points-to-an-object.md) 有关自动创建的详细信息连接点代理。  
  
> [!NOTE]
>  选件类 [CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md)**Add Class** 向导使用**Note**，当创建具有的控件\)时连接点。  如果您希望指定数量的手动联接，从 **CComDynamicUnkArray** 更改对 `CComUnkArray<`*n* `>`，其中 *n* 是的数字连接点必需。  
  
## 要求  
 **Header:** atlcom.h  
  
## 请参阅  
 [CComDynamicUnkArray Class](../../atl/reference/ccomdynamicunkarray-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)