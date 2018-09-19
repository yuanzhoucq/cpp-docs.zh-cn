---
title: CComEnum 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComEnum
- atlcom/ATL::CComEnum
dev_langs:
- C++
helpviewer_keywords:
- CComEnum class
ms.assetid: bff7dd7b-eb6e-4d6e-96ed-2706e66c8b3b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7f9dff61a62eec37a503b1c0018ead6dce33065a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46077108"
---
# <a name="ccomenum-class"></a>CComEnum 类

此类定义基于数组的 COM 枚举器对象。

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

*基本*<br/>
COM 枚举器接口。 请参阅[IEnumString](/windows/desktop/api/objidl/nn-objidl-ienumstring)有关的示例。

*piid*<br/>
一个指向枚举器接口的接口 ID。

*T*<br/>
枚举器接口所显示的项的类型。

*复制*<br/>
同构[复制策略类](../../atl/atl-copy-policy-classes.md)。

*ThreadModel*<br/>
类的线程模型。 此参数默认为你的项目中使用的全局对象线程模型。

## <a name="remarks"></a>备注

`CComEnum` 定义基于数组的 COM 枚举器对象。 此类是类似于[CComEnumOnSTL](../../atl/reference/ccomenumonstl-class.md)它可实现基于 c + + 标准库容器的枚举器。 使用此类的典型步骤如下所述。 有关详细信息，请参阅[ATL 集合和枚举器](../../atl/atl-collections-and-enumerators.md)。

## <a name="to-use-this-class"></a>若要使用此类：

- **typedef**的此类专用化。

- 使用**typedef**中的专用化的模板自变量作为`CComObject`。

- 创建的实例`CComObject`专用化。

- 通过调用枚举器对象初始化[CComEnumImpl::Init](../../atl/reference/ccomenumimpl-class.md#init)。

- 返回到客户端的枚举数接口。

## <a name="inheritance-hierarchy"></a>继承层次结构

`CComObjectRootBase`

`Base`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

[CComEnumImpl](../../atl/reference/ccomenumimpl-class.md)

`CComEnum`

## <a name="requirements"></a>要求

**标头：** atlcom.h

## <a name="example"></a>示例

如下所示的代码提供了用于创建和初始化的枚举器对象的可重用的函数。

[!code-cpp[NVC_ATL_COM#32](../../atl/codesnippet/cpp/ccomenum-class_1.h)]

此模板函数可用于实现`_NewEnum`属性的集合接口，如下所示：

[!code-cpp[NVC_ATL_COM#33](../../atl/codesnippet/cpp/ccomenum-class_2.h)]

此代码将创建**typedef**有关`CComEnum`公开的变体通过矢量`IEnumVariant`接口。 `CVariantArrayCollection`类只是专用化`CreateEnumerator`才能使用此类型和必需的自变量传递的枚举器对象。

## <a name="see-also"></a>请参阅

[类概述](../../atl/atl-class-overview.md)<br/>
[CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel)<br/>
[CComEnumImpl 类](../../atl/reference/ccomenumimpl-class.md)<br/>
[CComObjectRootEx 类](../../atl/reference/ccomobjectrootex-class.md)
