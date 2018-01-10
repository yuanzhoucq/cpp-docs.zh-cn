---
title: "CComEnumOnSTL 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComEnumOnSTL
- atlcom/ATL::CComEnumOnSTL
dev_langs: C++
helpviewer_keywords: CComEnumOnSTL class
ms.assetid: befe1a44-7a00-4f28-9a2e-cc0fa526643c
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d42d99baf154bc5434f2d771aeaabb71c5502b30
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="ccomenumonstl-class"></a>CComEnumOnSTL 类
此类定义一个基于 c + + 标准库集合的 COM 枚举器对象。  
  
## <a name="syntax"></a>语法  
  
```
template <class Base,
    const IID* piid, class T, class Copy, class CollType, class ThreadModel = CComObjectThreadModel>  
class ATL_NO_VTABLE CComEnumOnSTL : public IEnumOnSTLImpl<Base, piid,
 T,
    Copy,
 CollType>,
    public CComObjectRootEx<ThreadModel>
```  
  
#### <a name="parameters"></a>参数  
 `Base`  
 COM 枚举器 ( [IEnumXXXX](https://msdn.microsoft.com/library/ms680089.aspx)) 接口。  
  
 `piid`  
 指向的枚举器接口的接口 ID 的指针。  
  
 `T`  
 枚举器接口所显示的项类型。  
  
 `Copy`  
 A[复制策略](../../atl/atl-copy-policy-classes.md)类。  
  
 `CollType`  
 C + + 标准库容器类。  
  
## <a name="remarks"></a>备注  
 `CComEnumOnSTL`定义根据 c + + 标准库集合的 COM 枚举器对象。 此类可用于在其自身或结合[ICollectionOnSTLImpl](../../atl/reference/icollectiononstlimpl-class.md)。 使用此类的典型步骤如下所述。 有关详细信息，请参阅[ATL 集合和枚举数](../../atl/atl-collections-and-enumerators.md)。  
  
## <a name="to-use-this-class-with-icollectiononstlimpl"></a>将此类用于 ICollectionOnSTLImpl:  
  
- `typedef`此类的专用化。  
  
-   使用`typedef`的专用化中的最后一个模板参数作为`ICollectionOnSTLImpl`。  
  
 请参阅[ATL 集合和枚举数](../../atl/atl-collections-and-enumerators.md)有关示例。  
  
## <a name="to-use-this-class-independently-of-icollectiononstlimpl"></a>若要使用独立 ICollectionOnSTLImpl 于此类：  
  
- `typedef`此类的专用化。  
  
-   使用`typedef`中的专用化的模板自变量作为`CComObject`。  
  
-   创建的实例`CComObject`专用化。  
  
-   通过调用初始化的枚举器对象[IEnumOnSTLImpl::Init](../../atl/reference/ienumonstlimpl-class.md#init)。  
  
-   返回的枚举器接口返回到客户端。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `CComObjectRootBase`  
  
 `Base`  
  
 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)  
  
 [IEnumOnSTLImpl](../../atl/reference/ienumonstlimpl-class.md)  
  
 `CComEnumOnSTL`  
  
## <a name="requirements"></a>惠?  
 **标头：** atlcom.h  
  
## <a name="example"></a>示例  
 下面显示的代码提供泛型函数来处理的创建和初始化的枚举器对象：  
  
 [!code-cpp[NVC_ATL_COM#34](../../atl/codesnippet/cpp/ccomenumonstl-class_1.h)]  
  
 此模板函数可用于实现`_NewEnum`属性的集合接口如下所示：  
  
 [!code-cpp[NVC_ATL_COM#35](../../atl/codesnippet/cpp/ccomenumonstl-class_2.h)]  
  
 此代码将创建`typedef`为`CComEnumOnSTL`公开的向量`CComVariant`通过 s **IEnumVariant**接口。 **CVariantCollection**类只是专用化**CreateSTLEnumerator**要使用此类型的枚举器对象。  
  
## <a name="see-also"></a>请参阅  
 [IEnumOnSTLImpl](../../atl/reference/ienumonstlimpl-class.md)   
 [ATLCollections 示例： 演示 ICollectionOnSTLImpl、 CComEnumOnSTL 和自定义的复制策略类](../../visual-cpp-samples.md)   
 [类概述](../../atl/atl-class-overview.md)   
 [CComObjectRootEx 类](../../atl/reference/ccomobjectrootex-class.md)   
 [CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel)   
 [IEnumOnSTLImpl 类](../../atl/reference/ienumonstlimpl-class.md)
