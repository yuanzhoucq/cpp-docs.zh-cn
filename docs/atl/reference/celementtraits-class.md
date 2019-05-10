---
title: CElementTraits 类
ms.date: 11/04/2016
f1_keywords:
- CElementTraits
- atlcoll/ATL::CElementTraits
helpviewer_keywords:
- CElementTraits class
ms.assetid: 496528e5-7f80-4b45-be0c-6f646feb43c5
ms.openlocfilehash: 646b445aed93c9041932c60442f61792f5e1a7e8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62245763"
---
# <a name="celementtraits-class"></a>CElementTraits 类

此类是集合类用于为移动、 复制、 比较和哈希操作提供方法和函数。

## <a name="syntax"></a>语法

```
template<typename T>
class CElementTraits : public CDefaultElementTraits<T>
```

#### <a name="parameters"></a>参数

*T*<br/>
要存储在集合中的数据类型。

## <a name="remarks"></a>备注

此类提供默认静态函数和方法用于移动、 复制、 比较和哈希存储在集合类对象中的元素。 `CElementTraits` 通过集合类指定为这些操作的默认提供程序[CAtlArray](../../atl/reference/catlarray-class.md)， [CAtlList](../../atl/reference/catllist-class.md)， [CRBMap](../../atl/reference/crbmap-class.md)， [CRBMultiMap](../../atl/reference/crbmultimap-class.md)，并[CRBTree](../../atl/reference/crbtree-class.md)。

默认实现为简单数据类型就足够了，但如果集合类用于存储更复杂的对象，必须由用户提供的实现覆盖函数和方法。

有关详细信息，请参阅[ATL 集合类](../../atl/atl-collection-classes.md)。

## <a name="requirements"></a>要求

**标头：** atlcoll.h

## <a name="see-also"></a>请参阅

[CDefaultElementTraits 类](../../atl/reference/cdefaultelementtraits-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
