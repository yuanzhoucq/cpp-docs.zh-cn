---
title: "CComEnumImpl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.CComEnumImpl"
  - "ATL::CComEnumImpl"
  - "CComEnumImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComEnumImpl class"
ms.assetid: cc0d8e76-e608-46db-87cd-4c7161fe32d2
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# CComEnumImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类对枚举项存储在数组中的COM枚举器提供了接口实现。  
  
## 语法  
  
```  
  
      template <  
   class Base,  
   const IID* piid,  
   class T,  
   class Copy  
>  
class ATL_NO_VTABLE CComEnumImpl :   
   public Base  
```  
  
#### 参数  
 `Base`  
 COM枚举器 \([IEnumXXXX](https://msdn.microsoft.com/en-us/library/ms680089.aspx)\) 接口。  
  
 `piid`  
 对枚举器接口的接口ID的指针。  
  
 `T`  
 枚举器接口显示的项的类型。  
  
 `Copy`  
 同类 [复制策略类选件](../../atl/atl-copy-policy-classes.md)。  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CComEnumImpl::CComEnumImpl](../Topic/CComEnumImpl::CComEnumImpl.md)|构造函数。|  
|[CComEnumImpl::~CComEnumImpl](../Topic/CComEnumImpl::~CComEnumImpl.md)|该析构函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CComEnumImpl::Clone](../Topic/CComEnumImpl::Clone.md)|[IEnumXXXX::Clone](https://msdn.microsoft.com/en-us/library/ms690336.aspx)的实现。|  
|[CComEnumImpl::Init](../Topic/CComEnumImpl::Init.md)|初始化枚举数。|  
|[CComEnumImpl::Next](../Topic/CComEnumImpl::Next.md)|[IEnumXXXX::Next](https://msdn.microsoft.com/en-us/library/ms695273.aspx)的实现。|  
|[CComEnumImpl::Reset](../Topic/CComEnumImpl::Reset.md)|[IEnumXXXX::Reset](https://msdn.microsoft.com/en-us/library/ms693414.aspx)的实现。|  
|[CComEnumImpl::Skip](../Topic/CComEnumImpl::Skip.md)|[IEnumXXXX::Skip](https://msdn.microsoft.com/en-us/library/ms690392.aspx)的实现。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CComEnumImpl::m\_begin](../Topic/CComEnumImpl::m_begin.md)|对于第一项的指针数组中。|  
|[CComEnumImpl::m\_dwFlags](../Topic/CComEnumImpl::m_dwFlags.md)|复制标志通过 `Init`。|  
|[CComEnumImpl::m\_end](../Topic/CComEnumImpl::m_end.md)|为位置的指针在数组中的最后一项之外。|  
|[CComEnumImpl::m\_iter](../Topic/CComEnumImpl::m_iter.md)|对当前项的指针数组中。|  
|[CComEnumImpl::m\_spUnk](../Topic/CComEnumImpl::m_spUnk.md)|提供集合对象的 **IUnknown** 指针枚举。|  
  
## 备注  
 `CComEnumImpl` 对枚举项存储在数组中的COM枚举器提供了接口实现。  此选件类类似于 `IEnumOnSTLImpl` 选件类，提供基于STL容器的枚举器接口实现。  
  
> [!NOTE]
>  有关进一步差异的详细信息。`CComEnumImpl` 和 `IEnumOnSTLImpl`之间，请参见 [CComEnumImpl::Init](../Topic/CComEnumImpl::Init.md)。  
  
 通常，不需要通过派生创建自己的枚举数选件类派生自此接口实现。  如果要使用基于数组的一个由ATL提供的枚举数，更为常见的创建 [CComEnum](../../atl/reference/ccomenum-class.md)实例。  
  
 但是，因此，如果您需要提供自定义枚举数\(例如，显示接口除枚举数接口\)的一个，可以从此选件类派生。  在这种情况下，很可能需要重写 [CComEnumImpl::Clone](../Topic/CComEnumImpl::Clone.md) 方法提供自己的实现。  
  
 有关更多信息，请参见 [ATL 集合和枚举数](../../atl/atl-collections-and-enumerators.md)。  
  
## 继承层次结构  
 `Base`  
  
 `CComEnumImpl`  
  
## 要求  
 **Header:** atlcom.h  
  
## 请参阅  
 [IEnumOnSTLImpl Class](../../atl/reference/ienumonstlimpl-class.md)   
 [CComEnum Class](../../atl/reference/ccomenum-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)