---
title: CComEnumOnSTL 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComEnumOnSTL
- atlcom/ATL::CComEnumOnSTL
dev_langs:
- C++
helpviewer_keywords:
- CComEnumOnSTL class
ms.assetid: befe1a44-7a00-4f28-9a2e-cc0fa526643c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 89f811f476fb21d2880169c168671515c9d8caf9
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43223133"
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
 *基本*  
 COM 的枚举器。 请参阅[IEnumString](/windows/desktop/api/objidl/nn-objidl-ienumstring)有关的示例。 
  
 *piid*  
 一个指向枚举器接口的接口 ID。  
  
 *T*  
 枚举器接口所显示的项的类型。  
  
 *复制*  
 一个[复制策略](../../atl/atl-copy-policy-classes.md)类。  
  
 *CollType*  
 C + + 标准库容器类。  
  
## <a name="remarks"></a>备注  
 `CComEnumOnSTL` 定义基于 c + + 标准库集合的 COM 枚举器对象。 此类可以在自己或结合[ICollectionOnSTLImpl](../../atl/reference/icollectiononstlimpl-class.md)。 使用此类的典型步骤如下所述。 有关详细信息，请参阅[ATL 集合和枚举器](../../atl/atl-collections-and-enumerators.md)。  
  
## <a name="to-use-this-class-with-icollectiononstlimpl"></a>若要将此类与 ICollectionOnSTLImpl:  
  
- **typedef**的此类专用化。  
  
-   使用**typedef**作为最终模板参数中的专用化`ICollectionOnSTLImpl`。  
  
 请参阅[ATL 集合和枚举器](../../atl/atl-collections-and-enumerators.md)有关的示例。  
  
## <a name="to-use-this-class-independently-of-icollectiononstlimpl"></a>若要使用此独立于 ICollectionOnSTLImpl 类：  
  
- **typedef**的此类专用化。  
  
-   使用**typedef**中的专用化的模板自变量作为`CComObject`。  
  
-   创建的实例`CComObject`专用化。  
  
-   通过调用枚举器对象初始化[IEnumOnSTLImpl::Init](../../atl/reference/ienumonstlimpl-class.md#init)。  
  
-   返回到客户端的枚举数接口。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `CComObjectRootBase`  
  
 `Base`  
  
 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)  
  
 [IEnumOnSTLImpl](../../atl/reference/ienumonstlimpl-class.md)  
  
 `CComEnumOnSTL`  
  
## <a name="requirements"></a>要求  
 **标头：** atlcom.h  
  
## <a name="example"></a>示例  
 如下所示的代码提供了一个泛型函数以处理创建和初始化的枚举器对象：  
  
 [!code-cpp[NVC_ATL_COM#34](../../atl/codesnippet/cpp/ccomenumonstl-class_1.h)]  
  
 此模板函数可用于实现`_NewEnum`属性的集合接口，如下所示：  
  
 [!code-cpp[NVC_ATL_COM#35](../../atl/codesnippet/cpp/ccomenumonstl-class_2.h)]  
  
 此代码将创建**typedef**有关`CComEnumOnSTL`公开的矢量`CComVariant`s 通过`IEnumVariant`接口。 `CVariantCollection`类只是专用化`CreateSTLEnumerator`才能使用此类型的枚举器对象。  
  
## <a name="see-also"></a>请参阅  
 [IEnumOnSTLImpl](../../atl/reference/ienumonstlimpl-class.md)   
 [ATLCollections 示例： 演示 ICollectionOnSTLImpl 和 CComEnumOnSTL，自定义复制策略类](../../visual-cpp-samples.md)   
 [类概述](../../atl/atl-class-overview.md)   
 [CComObjectRootEx 类](../../atl/reference/ccomobjectrootex-class.md)   
 [CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel)   
 [IEnumOnSTLImpl 类](../../atl/reference/ienumonstlimpl-class.md)
