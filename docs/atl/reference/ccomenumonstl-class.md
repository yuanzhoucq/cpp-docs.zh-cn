---
title: CComEnumOnSTL 类
ms.date: 11/04/2016
f1_keywords:
- CComEnumOnSTL
- atlcom/ATL::CComEnumOnSTL
helpviewer_keywords:
- CComEnumOnSTL class
ms.assetid: befe1a44-7a00-4f28-9a2e-cc0fa526643c
ms.openlocfilehash: b0674d64b471318d972d209373e0d74af0fa77f5
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226589"
---
# <a name="ccomenumonstl-class"></a>CComEnumOnSTL 类

此类定义基于 c + + 标准库集合的 COM 枚举器对象。

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

*基座*<br/>
COM 枚举器。 有关示例，请参阅[IEnumString](/windows/win32/api/objidl/nn-objidl-ienumstring) 。

*piid*<br/>
指向枚举器接口的接口 ID 的指针。

*T*<br/>
枚举器接口公开的项的类型。

*复制*<br/>
[复制策略](../../atl/atl-copy-policy-classes.md)类。

*CollType*<br/>
C + + 标准库容器类。

## <a name="remarks"></a>备注

`CComEnumOnSTL`定义基于 c + + 标准库集合的 COM 枚举器对象。 此类可以单独使用，也可以与[ICollectionOnSTLImpl](../../atl/reference/icollectiononstlimpl-class.md)一起使用。 下面概述了使用此类的典型步骤。 有关详细信息，请参阅[ATL 集合和枚举](../../atl/atl-collections-and-enumerators.md)器。

## <a name="to-use-this-class-with-icollectiononstlimpl"></a>若要将此类与 ICollectionOnSTLImpl 一起使用：

- **`typedef`** 此类的专用化。

- 使用 **`typedef`** 作为专用化中的最终模板参数 `ICollectionOnSTLImpl` 。

有关示例，请参阅[ATL 集合和枚举](../../atl/atl-collections-and-enumerators.md)器。

## <a name="to-use-this-class-independently-of-icollectiononstlimpl"></a>若要单独使用此类，请使用 ICollectionOnSTLImpl：

- **`typedef`** 此类的专用化。

- 使用 **`typedef`** 作为专用化中的模板参数 `CComObject` 。

- 创建专用化的实例 `CComObject` 。

- 通过调用[IEnumOnSTLImpl：： Init](../../atl/reference/ienumonstlimpl-class.md#init)初始化枚举器对象。

- 将枚举器接口返回到客户端。

## <a name="inheritance-hierarchy"></a>继承层次结构

`CComObjectRootBase`

`Base`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

[IEnumOnSTLImpl](../../atl/reference/ienumonstlimpl-class.md)

`CComEnumOnSTL`

## <a name="requirements"></a>要求

**标头：** atlcom。h

## <a name="example"></a>示例

下面显示的代码提供了一个用于处理枚举器对象的创建和初始化的泛型函数：

[!code-cpp[NVC_ATL_COM#34](../../atl/codesnippet/cpp/ccomenumonstl-class_1.h)]

此模板函数可用于实现 `_NewEnum` 集合接口的属性，如下所示：

[!code-cpp[NVC_ATL_COM#35](../../atl/codesnippet/cpp/ccomenumonstl-class_2.h)]

此代码将创建 **`typedef`** 一个 `CComEnumOnSTL` ，它将 `CComVariant` 通过接口公开向量 `IEnumVariant` 。 `CVariantCollection`类只是专门 `CreateSTLEnumerator` 用于处理此类型的枚举器对象。

## <a name="see-also"></a>另请参阅

[IEnumOnSTLImpl](../../atl/reference/ienumonstlimpl-class.md)<br/>
[ATLCollections 示例：演示 ICollectionOnSTLImpl、CComEnumOnSTL 和自定义复制策略类](../../overview/visual-cpp-samples.md)<br/>
[类概述](../../atl/atl-class-overview.md)<br/>
[CComObjectRootEx 类](../../atl/reference/ccomobjectrootex-class.md)<br/>
[CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel)<br/>
[IEnumOnSTLImpl 类](../../atl/reference/ienumonstlimpl-class.md)
