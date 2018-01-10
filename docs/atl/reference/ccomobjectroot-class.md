---
title: "CComObjectRoot 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComObjectRoot
- atlcom/ATL::CComObjectRoot
dev_langs: C++
helpviewer_keywords: CComObjectRoot class
ms.assetid: f8797c38-6e73-4f67-85c2-71654cffa8eb
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3acd4d91082d79cff0e945f841389fb2428396f8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="ccomobjectroot-class"></a>CComObjectRoot 类
此 typedef [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)针对线程处理模型的服务器的默认模板。  
  
## <a name="syntax"></a>语法  
  
```
typedef CComObjectRootEx<CComObjectThreadModel> CComObjectRoot;
```  
  
## <a name="remarks"></a>备注  
 `CComObjectRoot`是`typedef`的[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)针对线程处理模型的服务器的默认模板。 因此[CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel)将引用，则[CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md)或[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)。  
  
 `CComObjectRootEx`处理非聚合和聚合对象的对象引用计数管理。 如果你的对象不正在聚合，并且如果你的对象进行了正在聚合包含指向未知的外部对象，它包含的对象引用计数。 对于聚合对象，`CComObjectRootEx`方法可以用于处理失败的内部对象构造，并保护中删除在发布内部接口的外部对象或内部对象删除。  
  
## <a name="requirements"></a>惠?  
 **标头：** atlcom.h  
  
## <a name="see-also"></a>请参阅  
 [CComObjectRootEx 类成员](http://msdn.microsoft.com/en-us/e3ce9c3d-9c8e-4fe5-b682-8e56740a0164)   
 [CComObjectRootEx 类](../../atl/reference/ccomobjectrootex-class.md)   
 [CComAggObject 类](../../atl/reference/ccomaggobject-class.md)   
 [CComObject 类](../../atl/reference/ccomobject-class.md)   
 [CComPolyObject 类](../../atl/reference/ccompolyobject-class.md)   
 [类概述](../../atl/atl-class-overview.md)
