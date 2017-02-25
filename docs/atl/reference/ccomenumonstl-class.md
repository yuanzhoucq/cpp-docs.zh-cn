---
title: "CComEnumOnSTL Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CComEnumOnSTL"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComEnumOnSTL class"
ms.assetid: befe1a44-7a00-4f28-9a2e-cc0fa526643c
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CComEnumOnSTL Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类定义了基于STL集合的COM enumerator对象。  
  
## 语法  
  
```  
  
      template <  
   class Base,  
   const IID* piid,  
   class T,  
   class Copy,  
   class CollType,  
   class ThreadModel = CComObjectThreadModel  
>  
class ATL_NO_VTABLE CComEnumOnSTL :  
   public IEnumOnSTLImpl<Base, piid, T, Copy, CollType>,  
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
 [复制策略](../../atl/atl-copy-policy-classes.md) 选件类。  
  
 `CollType`  
 STL容器选件类。  
  
## 备注  
 `CComEnumOnSTL` 定义基于STL集合的COM enumerator对象。  此选件类可以使用自己的或与 [ICollectionOnSTLImpl](../../atl/reference/icollectiononstlimpl-class.md)结合使用。  典型的步骤来使用此选件类下面概述。  有关更多信息，请参见 [ATL 集合和枚举数](../../atl/atl-collections-and-enumerators.md)。  
  
## 使用ICollectionOnSTLImpl的此选件类:  
  
-   `typedef` 此选件类的专用化。  
  
-   使用 `typedef` 为最终模板参数在 `ICollectionOnSTLImpl`的专用化。  
  
 有关示例 [ATL 集合和枚举数](../../atl/atl-collections-and-enumerators.md) 参见。  
  
## 独立ICollectionOnSTLImpl使用此选件类:  
  
-   `typedef` 此选件类的专用化。  
  
-   使用 `typedef` 用作模板参数在 `CComObject`的专用化。  
  
-   创建 `CComObject` 专用化的实例。  
  
-   通过调用 [IEnumOnSTLImpl::Init](../Topic/IEnumOnSTLImpl::Init.md)初始化枚举数对象。  
  
-   返回枚举数接口到客户端。  
  
## 继承层次结构  
 `CComObjectRootBase`  
  
 `Base`  
  
 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)  
  
 [IEnumOnSTLImpl](../../atl/reference/ienumonstlimpl-class.md)  
  
 `CComEnumOnSTL`  
  
## 要求  
 **Header:** atlcom.h  
  
## 示例  
 如下所示的代码提供泛型函数处理enumerator对象的创建和初始化:  
  
 [!code-cpp[NVC_ATL_COM#34](../../atl/codesnippet/CPP/ccomenumonstl-class_1.h)]  
  
 此模板函数来实现集合接口的 `_NewEnum` 属性如下所示:  
  
 [!code-cpp[NVC_ATL_COM#35](../../atl/codesnippet/CPP/ccomenumonstl-class_2.h)]  
  
 通过 **IEnumVariant** 接口公开 `CComVariant`的矢量的此代码创建 `CComEnumOnSTL` 的 `typedef`。  **CVariantCollection** 选件类专用 **CreateSTLEnumerator** 与此类型一起使用枚举数对象。  
  
## 请参阅  
 [IEnumOnSTLImpl](../../atl/reference/ienumonstlimpl-class.md)   
 [ATLCollections示例:演示ICollectionOnSTLImpl、CComEnumOnSTL和自定义复制策略类选件](../../top/visual-cpp-samples.md)   
 [Class Overview](../../atl/atl-class-overview.md)   
 [CComObjectRootEx Class](../../atl/reference/ccomobjectrootex-class.md)   
 [CComObjectThreadModel](../Topic/CComObjectThreadModel.md)   
 [IEnumOnSTLImpl Class](../../atl/reference/ienumonstlimpl-class.md)