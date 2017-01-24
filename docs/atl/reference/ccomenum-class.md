---
title: "CComEnum Class | Microsoft Docs"
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
  - "CComEnum"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComEnum class"
ms.assetid: bff7dd7b-eb6e-4d6e-96ed-2706e66c8b3b
caps.latest.revision: 20
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CComEnum Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类定义了基于数组的COM enumerator对象。  
  
## 语法  
  
```  
  
      template <  
   class Base,  
   const IID* piid,  
   class T,  
   class Copy,  
   class ThreadModel = CcomObjectThreadModel  
>  
class ATL_NO_VTABLE CComEnum :  
   public CComEnumImpl<Base, piid, T, Copy>,  
   public CComObjectRootEx< ThreadModel >  
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
  
 `ThreadModel`  
 选件类的线程模型。  此参数默认为用于项目的全局对象线程模型。  
  
## 备注  
 `CComEnum` 定义基于数组的COM enumerator对象。  实现基于STL容器的枚举数的此选件类类似于 [CComEnumOnSTL](../../atl/reference/ccomenumonstl-class.md)。  典型的步骤来使用此选件类下面概述。  有关更多信息，请参见 [ATL 集合和枚举数](../../atl/atl-collections-and-enumerators.md)。  
  
## 使用此选件类:  
  
-   `typedef` 此选件类的专用化。  
  
-   使用 `typedef` 用作模板参数在 `CComObject`的专用化。  
  
-   创建 `CComObject` 专用化的实例。  
  
-   通过调用 [CComEnumImpl::Init](../Topic/CComEnumImpl::Init.md)初始化枚举数对象。  
  
-   返回枚举数接口到客户端。  
  
## 继承层次结构  
 `CComObjectRootBase`  
  
 `Base`  
  
 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)  
  
 [CComEnumImpl](../../atl/reference/ccomenumimpl-class.md)  
  
 `CComEnum`  
  
## 要求  
 **Header:** atlcom.h  
  
## 示例  
 如下所示的代码用于创建和初始化enumerator对象提供可重用的功能。  
  
 [!code-cpp[NVC_ATL_COM#32](../../atl/codesnippet/CPP/ccomenum-class_1.h)]  
  
 此模板函数来实现集合接口的 `_NewEnum` 属性如下所示:  
  
 [!code-cpp[NVC_ATL_COM#33](../../atl/codesnippet/CPP/ccomenum-class_2.h)]  
  
 通过 **IEnumVariant** 接口公开 **VARIANT**的矢量的此代码创建 `CComEnum` 的 `typedef`。  **CVariantArrayCollection** 选件类专用 **CreateEnumerator** 与此类型一起使用枚举数对象传递必需的参数。  
  
## 请参阅  
 [Class Overview](../../atl/atl-class-overview.md)   
 [CComObjectThreadModel](../Topic/CComObjectThreadModel.md)   
 [CComEnumImpl Class](../../atl/reference/ccomenumimpl-class.md)   
 [CComObjectRootEx Class](../../atl/reference/ccomobjectrootex-class.md)