---
title: "CComCachedTearOffObject Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL::CComCachedTearOffObject"
  - "ATL.CComCachedTearOffObject"
  - "ATL.CComCachedTearOffObject<contained>"
  - "CComCachedTearOffObject"
  - "ATL::CComCachedTearOffObject<contained>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "缓存, ATL cached tear-off objects"
  - "CComCachedTearOffObject class"
ms.assetid: ae19507d-a1de-4dbc-a988-da9f75a50c95
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# CComCachedTearOffObject Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类实现拖曳接口的 [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509)。  
  
## 语法  
  
```  
  
      template <  
   class contained  
>  
class CComCachedTearOffObject : public IUnknown,  
   public CComObjectRootEx< contained::_ThreadModel::ThreadModelNoCS >  
```  
  
#### 参数  
 `contained`  
 您的拖曳选件类，从派生 `CComTearOffObjectBase`，您希望接口拖曳对象支持。  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CComCachedTearOffObject::CComCachedTearOffObject](../Topic/CComCachedTearOffObject::CComCachedTearOffObject.md)|构造函数。|  
|[CComCachedTearOffObject::~CComCachedTearOffObject](../Topic/CComCachedTearOffObject::~CComCachedTearOffObject.md)|该析构函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CComCachedTearOffObject::AddRef](../Topic/CComCachedTearOffObject::AddRef.md)|增加 `CComCachedTearOffObject` 对象的引用计数。|  
|[CComCachedTearOffObject::FinalConstruct](../Topic/CComCachedTearOffObject::FinalConstruct.md)|调用 `m_contained::FinalConstruct` \(拖曳选件类的方法）。|  
|[CComCachedTearOffObject::FinalRelease](../Topic/CComCachedTearOffObject::FinalRelease.md)|调用 `m_contained::FinalRelease` \(拖曳选件类的方法）。|  
|[CComCachedTearOffObject::QueryInterface](../Topic/CComCachedTearOffObject::QueryInterface.md)|返回指向 `CComCachedTearOffObject` 对象的 `IUnknown`，或者对请求的接口为拖曳选件类\(选件类 `contained`）。|  
|[CComCachedTearOffObject::Release](../Topic/CComCachedTearOffObject::Release.md)|如果引用计数为0，`CComCachedTearOffObject` 递减对象的引用计数并销毁它。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CComCachedTearOffObject::m\_contained](../Topic/CComCachedTearOffObject::m_contained.md)|从从派生的 `CComContainedObject` 对象拖曳选件类\(选件类 `contained`）。|  
  
## 备注  
 拖曳接口的`CComCachedTearOffObject` 实现 [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509)。  此选件类与 `CComTearOffObject` 不同 `CComCachedTearOffObject` 具有自己的 **IUnknown**，与所有者对象的 **IUnknown** \(所有者是拖曳创建的对象）。  在其引用计数为零时，`CComCachedTearOffObject` 保持自己对其 **IUnknown** 的计数和删除它。  但是，因此，如果您为任何其他查询的拖曳接口，对象的 **IUnknown** 将增加所有者的引用计数。  
  
 如果实现拖曳的 `CComCachedTearOffObject` 对象实例化，因此，拖曳接口为再次查询，重用同一 `CComCachedTearOffObject` 对象。  相反，因此，如果 `CComTearOffObject` 实现的拖曳接口为通过所有者对象被再次查询，另一 `CComTearOffObject` 将实例化。  
  
 所有者选件类必须实现 `FinalRelease`，并调用缓存的 **IUnknown** 的 **Release**`CComCachedTearOffObject`的，将递减其引用计数。  这将导致`CComCachedTearOffObject`的 `FinalRelease` 调用和删除拖曳。  
  
## 继承层次结构  
 `CComObjectRootBase`  
  
 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)  
  
 `IUnknown`  
  
 `CComCachedTearOffObject`  
  
## 要求  
 **Header:** atlcom.h  
  
## 请参阅  
 [CComTearOffObject Class](../../atl/reference/ccomtearoffobject-class.md)   
 [CComObjectRootEx Class](../../atl/reference/ccomobjectrootex-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)