---
title: "IEnumOnSTLImpl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "IEnumOnSTLImpl"
  - "ATL.IEnumOnSTLImpl"
  - "ATL::IEnumOnSTLImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IEnumOnSTLImpl class"
ms.assetid: 1789e77b-88b8-447d-a490-806b918912ce
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# IEnumOnSTLImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类定义了基于STL集合的枚举数接口。  
  
## 语法  
  
```  
  
      template <  
   class Base,  
   const IID* piid,  
   class T,  
   class Copy,  
   class CollType  
>  
class ATL_NO_VTABLE IEnumOnSTLImpl :  
   public Base  
```  
  
#### 参数  
 `Base`  
 A COM 枚举器 \([IEnumXXXX](https://msdn.microsoft.com/en-us/library/ms680089.aspx)\) 接口。  
  
 `piid`  
 对枚举器接口的接口ID的指针。  
  
 `T`  
 枚举器接口显示的项的类型。  
  
 `Copy`  
 [复制策略类选件](../../atl/atl-copy-policy-classes.md)。  
  
 `CollType`  
 STL容器选件类。  
  
## 成员  
  
### 公共方法  
  
|名称|描述|  
|--------|--------|  
|[IEnumOnSTLImpl::Clone](../Topic/IEnumOnSTLImpl::Clone.md)|[IEnumXXXX::Clone](https://msdn.microsoft.com/en-us/library/ms690336.aspx) 的实现。|  
|[IEnumOnSTLImpl::Init](../Topic/IEnumOnSTLImpl::Init.md)|初始化枚举数。|  
|[IEnumOnSTLImpl::Next](../Topic/IEnumOnSTLImpl::Next.md)|[IEnumXXXX::Next](https://msdn.microsoft.com/en-us/library/ms695273.aspx) 的实现。|  
|[IEnumOnSTLImpl::Reset](../Topic/IEnumOnSTLImpl::Reset.md)|[IEnumXXXX::Reset](https://msdn.microsoft.com/en-us/library/ms693414.aspx) 的实现。|  
|[IEnumOnSTLImpl::Skip](../Topic/IEnumOnSTLImpl::Skip.md)|[IEnumXXXX::Skip](https://msdn.microsoft.com/en-us/library/ms690392.aspx) 的实现。|  
  
### 公共数据成员  
  
|名称|描述|  
|--------|--------|  
|[IEnumOnSTLImpl::m\_iter](../Topic/IEnumOnSTLImpl::m_iter.md)|表示在集合的枚举数的当前位置的迭代器。|  
|[IEnumOnSTLImpl::m\_pcollection](../Topic/IEnumOnSTLImpl::m_pcollection.md)|指针到包含项STL容器将枚举。|  
|[IEnumOnSTLImpl::m\_spUnk](../Topic/IEnumOnSTLImpl::m_spUnk.md)|提供集合对象的 **IUnknown** 指针。|  
  
## 备注  
 `IEnumOnSTLImpl` 对枚举项在一个STL兼容容器存储的COM枚举器提供了接口实现。  此选件类类似于 [CComEnumImpl](../../atl/reference/ccomenumimpl-class.md) 选件类，是根据数组的枚举器接口提供的实现。  
  
> [!NOTE]
>  请参见 [CComEnumImpl::Init](../Topic/CComEnumImpl::Init.md) 有关进一步差异的详细信息。`CComEnumImpl` 和 `IEnumOnSTLImpl`之间。  
  
 通常，不需要通过派生创建自己的枚举数选件类派生自此接口实现。  如果要使用基于STL容器的一个由ATL提供的枚举数，更为常见的创建 [CComEnumOnSTL](../../atl/reference/ccomenumonstl-class.md)实例，或者通过创建派生返回枚举数从 [ICollectionOnSTLImpl](../../atl/reference/icollectiononstlimpl-class.md)的集合选件类。  
  
 但是，因此，如果您需要提供自定义枚举数\(例如，显示接口除枚举数接口\)的一个，可以从此选件类派生。  在这种情况下很可能需要重写 [克隆](../Topic/IEnumOnSTLImpl::Clone.md) 方法提供自己的实现。  
  
## 继承层次结构  
 `Base`  
  
 `IEnumOnSTLImpl`  
  
## 要求  
 **Header:** atlcom.h  
  
## 请参阅  
 [Class Overview](../../atl/atl-class-overview.md)