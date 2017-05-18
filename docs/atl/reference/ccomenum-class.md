---
title: "CComEnum 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComEnum
- atlcom/ATL::CComEnum
dev_langs:
- C++
helpviewer_keywords:
- CComEnum class
ms.assetid: bff7dd7b-eb6e-4d6e-96ed-2706e66c8b3b
caps.latest.revision: 20
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5a0c6a1062330f952bb8fa52bc934f6754465513
ms.openlocfilehash: 72c172d7a619bb4fd1bd265e465653b691c0bc7b
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="ccomenum-class"></a>CComEnum 类
此类定义一个基于数组的 COM 枚举器对象。  
  
## <a name="syntax"></a>语法  
  
```
template <class Base,
    const IID* piid, class T, class Copy, class ThreadModel = CcomObjectThreadModel>  
class ATL_NO_VTABLE CComEnum : public CComEnumImpl<Base, piid,
 T,
    Copy>,
 public CComObjectRootEx<ThreadModel>
```  
  
#### <a name="parameters"></a>参数  
 `Base`  
 COM 枚举器 ( [IEnumXXXX](https://msdn.microsoft.com/library/ms680089.aspx)) 接口。  
  
 `piid`  
 指向的枚举器接口的接口 ID 的指针。  
  
 `T`  
 枚举器接口所显示的项的类型。  
  
 `Copy`  
 同构[复制策略类](../../atl/atl-copy-policy-classes.md)。  
  
 `ThreadModel`  
 此类线程处理模型。 此参数默认为您的项目中使用的全局对象线程模型。  
  
## <a name="remarks"></a>备注  
 `CComEnum`定义基于数组的 COM 枚举器对象。 此类是类似于[CComEnumOnSTL](../../atl/reference/ccomenumonstl-class.md)用来实现基于 c + + 标准库容器的枚举数。 使用此类的典型步骤如下所述。 有关详细信息，请参阅[ATL 集合和枚举数](../../atl/atl-collections-and-enumerators.md)。  
  
## <a name="to-use-this-class"></a>若要使用此类︰  
  
- `typedef`此类的专用化。  
  
-   使用`typedef`作为中的专用化的模板参数`CComObject`。  
  
-   创建的实例`CComObject`专用化。  
  
-   通过调用初始化枚举器对象[CComEnumImpl::Init](../../atl/reference/ccomenumimpl-class.md#init)。  
  
-   返回的枚举器接口返回到客户端。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `CComObjectRootBase`  
  
 `Base`  
  
 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)  
  
 [CComEnumImpl](../../atl/reference/ccomenumimpl-class.md)  
  
 `CComEnum`  
  
## <a name="requirements"></a>要求  
 **标头︰** atlcom.h  
  
## <a name="example"></a>示例  
 提供用于创建和初始化的枚举器对象的可重用函数如下所示的代码。  
  
 [!code-cpp[NVC_ATL_COM&#32;](../../atl/codesnippet/cpp/ccomenum-class_1.h)]  
  
 此模板函数可用于实现`_NewEnum`属性的集合接口如下所示︰  
  
 [!code-cpp[NVC_ATL_COM 第&33;](../../atl/codesnippet/cpp/ccomenum-class_2.h)]  
  
 此代码将创建`typedef`为`CComEnum`公开的矢量**VARIANT**通过 s **IEnumVariant**接口。 **CVariantArrayCollection**类只是专用化**CreateEnumerator**才能使用此类型和必需的参数传递的枚举器对象。  
  
## <a name="see-also"></a>另请参阅  
 [类概述](../../atl/atl-class-overview.md)   
 [CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel)   
 [CComEnumImpl 类](../../atl/reference/ccomenumimpl-class.md)   
 [CComObjectRootEx 类](../../atl/reference/ccomobjectrootex-class.md)

