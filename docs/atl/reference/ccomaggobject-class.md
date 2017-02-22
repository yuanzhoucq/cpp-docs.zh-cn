---
title: "CComAggObject Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL::CComAggObject<contained>"
  - "ATL.CComAggObject"
  - "ATL.CComAggObject<contained>"
  - "CComAggObject"
  - "ATL::CComAggObject"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "aggregate objects [C++], 在 ATL 中"
  - "aggregation [C++], ATL 对象"
  - "CComAggObject class"
ms.assetid: 7aa90d69-d399-477b-880d-e2cdf0ef7881
caps.latest.revision: 29
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 32
---
# CComAggObject Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类实现一个复合对象的 [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) 接口。  按照定义，一个聚合的对象处于一外部对象中。  `CComAggObject` 选件类类似于 [CComObject Class](../../atl/reference/ccomobject-class.md)，除此之外，显示可直接访问的外部客户端的接口。  
  
## 语法  
  
```  
  
      template<  
   class contained  
>  
class CComAggObject :  
   public IUnknown, public CComObjectRootEx  
   < contained::_ThreadModel::ThreadModelNoCS >  
```  
  
#### 参数  
 `contained`  
 您的选件类，从派生 [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) 或 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)，以及从任何其他接口包含在对象若要支持。  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CComAggObject::CComAggObject](../Topic/CComAggObject::CComAggObject.md)|构造函数。|  
|[CComAggObject::~CComAggObject](../Topic/CComAggObject::~CComAggObject.md)|该析构函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CComAggObject::AddRef](../Topic/CComAggObject::AddRef.md)|递增合成对象的引用计数。|  
|[CComAggObject::CreateInstance](../Topic/CComAggObject::CreateInstance.md)|此静态函数使您得以创建新的 **CComAggObject\<** `contained`**\>** 对象，而无需开销 [CoCreateInstance](http://msdn.microsoft.com/library/windows/desktop/ms686615)。|  
|[CComAggObject::FinalConstruct](../Topic/CComAggObject::FinalConstruct.md)|执行 `m_contained`的最终初始化。|  
|[CComAggObject::FinalRelease](../Topic/CComAggObject::FinalRelease.md)|执行 `m_contained`的最终损坏。|  
|[CComAggObject::QueryInterface](../Topic/CComAggObject::QueryInterface.md)|检索指向请求的接口。|  
|[CComAggObject::Release](../Topic/CComAggObject::Release.md)|递减在合成对象的引用计数。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CComAggObject::m\_contained](../Topic/CComAggObject::m_contained.md)|`IUnknown` 调用委托给外部未知。|  
  
## 备注  
 一个复合对象的`CComAggObject` 实现 [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509)。  `CComAggObject` 具有自己的 **IUnknown** 接口，与外部对象的 **IUnknown** 接口，并维护自己引用计数。  
  
 有关摘要的更多信息，请参见文章 [ATL COM对象的基本知识](../../atl/fundamentals-of-atl-com-objects.md)。  
  
## 继承层次结构  
 `CComObjectRootBase`  
  
 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)  
  
 `IUnknown`  
  
 `CComAggObject`  
  
## 要求  
 **Header:** atlcom.h  
  
## 请参阅  
 [CComObject Class](../../atl/reference/ccomobject-class.md)   
 [CComPolyObject Class](../../atl/reference/ccompolyobject-class.md)   
 [DECLARE\_AGGREGATABLE](../Topic/DECLARE_AGGREGATABLE.md)   
 [DECLARE\_ONLY\_AGGREGATABLE](../Topic/DECLARE_ONLY_AGGREGATABLE.md)   
 [DECLARE\_NOT\_AGGREGATABLE](../Topic/DECLARE_NOT_AGGREGATABLE.md)   
 [Class Overview](../../atl/atl-class-overview.md)