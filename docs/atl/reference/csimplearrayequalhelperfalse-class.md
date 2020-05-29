---
title: CSimpleArrayEqualHelperFalse 类
ms.date: 11/04/2016
f1_keywords:
- CSimpleArrayEqualHelperFalse
- ATLSIMPCOLL/ATL::CSimpleArrayEqualHelperFalse
- ATLSIMPCOLL/ATL::CSimpleArrayEqualHelperFalse::IsEqual
helpviewer_keywords:
- CSimpleArrayEqualHelperFalse class
ms.assetid: 6918af6f-d23d-49eb-8482-c44272f5ffeb
ms.openlocfilehash: 5eca3145d64895e34b599fbf83834af142b65973
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330887"
---
# <a name="csimplearrayequalhelperfalse-class"></a>CSimpleArrayEqualHelperFalse 类

此类是[CSimpleArray](../../atl/reference/csimplearray-class.md)类的帮助程序。

## <a name="syntax"></a>语法

```
template <class T>
class CSimpleArrayEqualHelperFalse
```

#### <a name="parameters"></a>参数

*T*<br/>
派生类。

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CSimplearray 平等帮助者False：：是平等的](#isequal)|（静态）返回 false。|

## <a name="remarks"></a>备注

此特征类是对类的补充`CSimpleArray`。 它总是返回 false，此外，如果引用 false，则调用`ATLASSERT`false。 在相等性测试定义不充分的情况下，此类允许包含元素的数组对大多数方法正确运行，但对于依赖于[CSimplearray：：find](../../atl/reference/csimplearray-class.md#find)等方法，以定义良好的方式失败。

## <a name="requirements"></a>要求

**标题：** atlsimpcoll.h

## <a name="csimplearrayequalhelperfalseisequal"></a><a name="isequal"></a>CSimplearray 平等帮助者False：：是平等的

返回 false。

```
static bool IsEqual(const T&, const T&);
```

### <a name="return-value"></a>返回值

返回 false。

### <a name="remarks"></a>备注

此方法始终返回 false，如果引用，`ATLASSERT`则调用 false 参数。 目的是`CSimpleArrayEqualHelperFalse::IsEqual`在未充分定义相等性测试时，强制使用比较的方法以定义明确的方式失败。

## <a name="see-also"></a>另请参阅

[CSimpleArrayEqualHelper 类](../../atl/reference/csimplearrayequalhelper-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
