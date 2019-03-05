---
title: CAutoPtrArray 类
ms.date: 11/04/2016
f1_keywords:
- CAutoPtrArray
- ATLCOLL/ATL::CAutoPtrArray
- ATLCOLL/ATL::CAutoPtrArray::CAutoPtrArray
helpviewer_keywords:
- CAutoPtrArray class
ms.assetid: 880a70da-8c81-4427-8ac6-49aa8d424244
ms.openlocfilehash: beb0184a9945990b8d92efe03d4f54baa76ca380
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57298901"
---
# <a name="cautoptrarray-class"></a>CAutoPtrArray 类

构造的智能指针的数组时，此类提供了有用的方法。

> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类和其成员。

## <a name="syntax"></a>语法

```
template <typename E>
class CAutoPtrArray : public CAtlArray<
                        ATL::CAutoPtr<E>,
                        CAutoPtrElementTraits<E>>
```

#### <a name="parameters"></a>参数

*E*<br/>
指针类型。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CAutoPtrArray::CAutoPtrArray](#cautoptrarray)|构造函数。|

## <a name="remarks"></a>备注

此类提供构造函数，并派生方法从[CAtlArray](../../atl/reference/catlarray-class.md)并[CAutoPtrElementTraits](../../atl/reference/cautoptrelementtraits-class.md)来帮助存储智能指针集合类对象的创建。

有关详细信息，请参阅[ATL 集合类](../../atl/atl-collection-classes.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

`CAtlArray`

`CAutoPtrArray`

## <a name="requirements"></a>要求

**标头：** atlcoll.h

##  <a name="cautoptrarray"></a>  CAutoPtrArray::CAutoPtrArray

构造函数。

```
CAutoPtrArray() throw();
```

### <a name="remarks"></a>备注

初始化智能指针数组。

## <a name="see-also"></a>请参阅

[CAtlArray 类](../../atl/reference/catlarray-class.md)<br/>
[CAutoPtrElementTraits 类](../../atl/reference/cautoptrelementtraits-class.md)<br/>
[CAutoPtrList 类](../../atl/reference/cautoptrlist-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
