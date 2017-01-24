---
title: "CComContainedObject Class | Microsoft Docs"
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
  - "CComContainedObject"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "aggregate objects [C++], 在 ATL 中"
  - "aggregation [C++], ATL 对象"
  - "CComContainedObject class"
ms.assetid: e8616b41-c200-47b8-bf2c-fb9f713ebdad
caps.latest.revision: 20
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CComContainedObject Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类通过委托实现 [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) 对所有者对象的 **IUnknown**。  
  
> [!IMPORTANT]
>  此选件类及其成员不能在Windows运行时执行的应用程序。  
  
## 语法  
  
```  
  
      template<  
class Base   
>  
class CComContainedObject :  
public Base  
```  
  
#### 参数  
 `Base`  
 您的选件类，从派生 [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) 或 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)。  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CComContainedObject::CComContainedObject](../Topic/CComContainedObject::CComContainedObject.md)|构造函数。  初始化成员的指针所有者对象的 `IUnknown`。|  
|[CComContainedObject::~CComContainedObject](../Topic/CComContainedObject::~CComContainedObject.md)|该析构函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CComContainedObject::AddRef](../Topic/CComContainedObject::AddRef.md)|递增所有者对象的引用计数。|  
|[CComContainedObject::GetControllingUnknown](../Topic/CComContainedObject::GetControllingUnknown.md)|检索所有者对象的 `IUnknown`。|  
|[CComContainedObject::QueryInterface](../Topic/CComContainedObject::QueryInterface.md)|检索指向在所有者对象请求的接口。|  
|[CComContainedObject::Release](../Topic/CComContainedObject::Release.md)|递减在所有者对象的引用计数。|  
  
## 备注  
 ATL在选件类 [CComAggObject](../../atl/reference/ccomaggobject-class.md)、 [CComPolyObject](../../atl/reference/ccompolyobject-class.md)和 [CComCachedTearOffObject](../../atl/reference/ccomcachedtearoffobject-class.md)使用 `CComContainedObject`。  `CComContainedObject` 通过委托实现 [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) 对所有者对象的 **IUnknown**。  （所有者是摘要的外部对象，或对象拖曳接口被创建。\) `CComContainedObject` 调用`CComObjectRootEx`的 `OuterQueryInterface`、 `OuterAddRef`和 `OuterRelease`，所有继承通过 `Base`。  
  
## 继承层次结构  
 `Base`  
  
 `CComContainedObject`  
  
## 要求  
 **Header:** atlcom.h  
  
## 请参阅  
 [Class Overview](../../atl/atl-class-overview.md)