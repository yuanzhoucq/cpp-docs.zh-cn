---
title: "CComObject Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.CComObject<Base>"
  - "ATL::CComObject"
  - "ATL::CComObject<Base>"
  - "ATL.CComObject"
  - "CComObject"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComObject class"
ms.assetid: e2b6433b-6349-4749-b4bc-acbd7a22c8b0
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# CComObject Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类实现一nonaggregated对象的 **IUnknown**。  
  
## 语法  
  
```  
  
      template<  
   class Base   
>  
class CComObject :  
   public Base  
```  
  
#### 参数  
 `Base`  
 您的选件类，从派生 [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) 或 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)，以及从任何其他接口包含在对象若要支持。  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CComObject::CComObject](../Topic/CComObject::CComObject.md)|构造函数。|  
|[CComObject::~CComObject](../Topic/CComObject::~CComObject.md)|该析构函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CComObject::AddRef](../Topic/CComObject::AddRef.md)|递增对象的引用计数。|  
|[CComObject::CreateInstance](../Topic/CComObject::CreateInstance.md)|（静态）创建新的 `CComObject` 对象。|  
|[CComObject::QueryInterface](../Topic/CComObject::QueryInterface.md)|检索指向请求的接口。|  
|[CComObject::Release](../Topic/CComObject::Release.md)|在递减对象的引用计数。|  
  
## 备注  
 一nonaggregated对象的`CComObject` 实现 [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509)。  但是，对 `QueryInterface`，`AddRef`，并且，**Release** 将委托给 `CComObjectRootEx`。  
  
 有关使用 `CComObject`的更多信息，请参见文章 [ATL COM对象的基本知识](../../atl/fundamentals-of-atl-com-objects.md)。  
  
## 继承层次结构  
 `Base`  
  
 `CComObject`  
  
## 要求  
 **Header:** atlcom.h  
  
## 请参阅  
 [CComAggObject Class](../../atl/reference/ccomaggobject-class.md)   
 [CComPolyObject Class](../../atl/reference/ccompolyobject-class.md)   
 [DECLARE\_AGGREGATABLE](../Topic/DECLARE_AGGREGATABLE.md)   
 [DECLARE\_NOT\_AGGREGATABLE](../Topic/DECLARE_NOT_AGGREGATABLE.md)   
 [Class Overview](../../atl/atl-class-overview.md)