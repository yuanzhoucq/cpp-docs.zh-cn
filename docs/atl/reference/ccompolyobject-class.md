---
title: "CComPolyObject Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CComPolyObject"
  - "ATL.CComPolyObject<contained>"
  - "ATL::CComPolyObject"
  - "ATL::CComPolyObject<contained>"
  - "ATL.CComPolyObject"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "aggregate objects [C++], 在 ATL 中"
  - "aggregation [C++], ATL 对象"
  - "CComPolyObject class"
ms.assetid: eaf67c18-e855-48ca-9b15-f1df3106121b
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# CComPolyObject Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类实现合成或nonaggregated对象的 **IUnknown**。  
  
## 语法  
  
```  
  
      template<  
   class contained   
>  
class CComPolyObject : public IUnknown, public CComObjectRootEx  
   < contained::_ThreadModel::ThreadModelNoCS >  
```  
  
#### 参数  
 `contained`  
 您的选件类，从派生 [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) 或 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)，以及从任何其他接口包含在对象若要支持。  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CComPolyObject::CComPolyObject](../Topic/CComPolyObject::CComPolyObject.md)|构造函数。|  
|[CComPolyObject::~CComPolyObject](../Topic/CComPolyObject::~CComPolyObject.md)|该析构函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CComPolyObject::AddRef](../Topic/CComPolyObject::AddRef.md)|递增对象的引用计数。|  
|[CComPolyObject::CreateInstance](../Topic/CComPolyObject::CreateInstance.md)|（静态）使您得以创建新的 **CComPolyObject\<** `contained`**\>** 对象，而无需开销 [CoCreateInstance](http://msdn.microsoft.com/library/windows/desktop/ms686615)。|  
|[CComPolyObject::FinalConstruct](../Topic/CComPolyObject::FinalConstruct.md)|执行 `m_contained`的最终初始化。|  
|[CComPolyObject::FinalRelease](../Topic/CComPolyObject::FinalRelease.md)|执行 `m_contained`的最终损坏。|  
|[CComPolyObject::QueryInterface](../Topic/CComPolyObject::QueryInterface.md)|检索指向请求的接口。|  
|[CComPolyObject::Release](../Topic/CComPolyObject::Release.md)|递减对象的引用计数。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CComPolyObject::m\_contained](../Topic/CComPolyObject::m_contained.md)|**IUnknown** 调用委托给外部未知，如果对象是聚合或对对象的 **IUnknown** 对象是否不聚合。|  
  
## 备注  
 `CComPolyObject` 实现合成或nonaggregated对象的 [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509)。  
  
 当 `CComPolyObject` 创建实例时，外部未知的值进行检查。  如果是 **NULL**，**IUnknown** 为一nonaggregated对象实现。  如果外部未知不是 **NULL**，**IUnknown** 为一个复合的对象实现。  
  
 使用 `CComPolyObject` 的优点是您避免为 [CComAggObject](../../atl/reference/ccomaggobject-class.md) 和 [CComObject](../../atl/reference/ccomobject-class.md) 在的模块处理合成和nonaggregated大小写。  一个 `CComPolyObject` 对象处理两种情况。  这意味着只有一个副本的vtable和函数的一个副本存在于您的模块。  如果vtable大，则可以显着降低您的模块范围。  但是，因此，如果vtable很小，使用 `CComPolyObject` 从而导致一个稍微大的模块范围，因为它没有为一个复合的或nonaggregated对象转换，如 `CComAggObject` 和 `CComObject`。  
  
 如果 `DECLARE_POLY_AGGREGATABLE` 宏在对象类定义中指定，`CComPolyObject` 将用于创建自己的对象。  如果使用ATL项目向导创建完整的控件或Internet Explorer控件，`DECLARE_POLY_AGGREGATABLE` 将自动声明。  
  
 如果聚合，`CComPolyObject` 对象都有自己的 **IUnknown**，与外部对象的 **IUnknown**，并维护自己引用计数。  `CComPolyObject` 使用 [CComContainedObject](../../atl/reference/ccomcontainedobject-class.md) 委托给外部未知。  
  
 有关摘要的更多信息，请参见文章 [ATL COM对象的基本知识](../../atl/fundamentals-of-atl-com-objects.md)。  
  
## 继承层次结构  
 `CComObjectRootBase`  
  
 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)  
  
 `IUnknown`  
  
 `CComPolyObject`  
  
## 要求  
 **Header:** atlcom.h  
  
## 请参阅  
 [CComObjectRootEx Class](../../atl/reference/ccomobjectrootex-class.md)   
 [DECLARE\_POLY\_AGGREGATABLE](../Topic/DECLARE_POLY_AGGREGATABLE.md)   
 [Class Overview](../../atl/atl-class-overview.md)