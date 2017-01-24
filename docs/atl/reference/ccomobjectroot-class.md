---
title: "CComObjectRoot Class | Microsoft Docs"
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
  - "CComObjectRoot"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComObjectRoot class"
ms.assetid: f8797c38-6e73-4f67-85c2-71654cffa8eb
caps.latest.revision: 17
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CComObjectRoot Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md) 此typedef在服务器的默认线程模型templatized。  
  
## 语法  
  
```  
  
typedef CComObjectRootEx<CComObjectThreadModel> CComObjectRoot;  
  
```  
  
## 备注  
 `CComObjectRoot` 是 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)`typedef` templatized在服务器的默认线程模型。  因此 [CComObjectThreadModel](../Topic/CComObjectThreadModel.md) 将引用 [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) 或 [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)。  
  
 `CComObjectRootEx` 处理对象引用nonaggregated和聚合的对象的计数管理。  它保留对象引用计数，如果您的对象不进行聚合，并存储指针给外部未知，如果您的对象进行聚合。  对聚合的对象，`CComObjectRootEx` 方法可用于处理内部对象的失败到构造的，因此，防止删除的外部对象，释放内部接口或内部对象被删除。  
  
## 要求  
 **Header:** atlcom.h  
  
## 请参阅  
 [CComObjectRootEx Class Members](http://msdn.microsoft.com/zh-cn/e3ce9c3d-9c8e-4fe5-b682-8e56740a0164)   
 [CComObjectRootEx Class](../../atl/reference/ccomobjectrootex-class.md)   
 [CComAggObject Class](../../atl/reference/ccomaggobject-class.md)   
 [CComObject Class](../../atl/reference/ccomobject-class.md)   
 [CComPolyObject Class](../../atl/reference/ccompolyobject-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)