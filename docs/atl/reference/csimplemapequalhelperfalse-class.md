---
title: CSimpleMapEqualHelperFalse 类
ms.date: 11/04/2016
f1_keywords:
- CSimpleMapEqualHelperFalse
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelperFalse
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelperFalse::IsEqualKey
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelperFalse::IsEqualValue
helpviewer_keywords:
- CSimpleMapEqualHelperFalse class
ms.assetid: a873eea3-e130-45cc-a476-61ee79511c3b
ms.openlocfilehash: b6bf1d4e3be849004e13e593fb5f4b5cb87f8123
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330731"
---
# <a name="csimplemapequalhelperfalse-class"></a>CSimpleMapEqualHelperFalse 类

此类是[CSimpleMap](../../atl/reference/csimplemap-class.md)类的帮助程序。

## <a name="syntax"></a>语法

```
template <class TKey, class TVal>
class CSimpleMapEqualHelperFalse
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[C 简单映射平等帮助者False：：是平等密钥](#isequalkey)|（静态）测试两个键的相等性。|
|[C 简单映射等值帮助者False：：等于值](#isequalvalue)|（静态）返回 false。|

## <a name="remarks"></a>备注

此特征类是对`CSimpleMap`类的补充。 它提供了一种比较`CSimpleMap`对象中包含的两个元素的方法，特别是两个值元素或两个键元素。

值比较将始终返回 false，此外，如果引用该参数`ATLASSERT`，则调用该参数为 false。 在相等性测试定义不充分的情况下，此类允许包含键/值对的映射在大多数方法中正常运行，但对于依赖于[CSimpleMap：：FindVal](../../atl/reference/csimplemap-class.md#findval)等方法，以定义良好的方式失败。

## <a name="requirements"></a>要求

**标题：** atlsimpcoll.h

## <a name="csimplemapequalhelperfalseisequalkey"></a><a name="isequalkey"></a>C 简单映射平等帮助者False：：是平等密钥

测试两个键的相等性。

```
static bool IsEqualKey(const TKey& k1, const TKey& k2);
```

### <a name="parameters"></a>参数

*k1*<br/>
第一个键。

*k2*<br/>
第二个键。

### <a name="return-value"></a>返回值

如果键相等，则返回 true，否则为 false。

### <a name="remarks"></a>备注

此方法调用[CSimplearray 平等帮助器](../../atl/reference/csimplearrayequalhelper-class.md)。

## <a name="csimplemapequalhelperfalseisequalvalue"></a><a name="isequalvalue"></a>C 简单映射等值帮助者False：：等于值

返回 false。

```
static bool IsEqualValue(const TVal&, const TVal&);
```

### <a name="return-value"></a>返回值

返回 false。

### <a name="remarks"></a>备注

此方法始终返回 false，如果引用它`ATLASSERT`，则调用 false 参数。 目的是`CSimpleMapEqualHelperFalse::IsEqualValue`在未充分定义相等性测试时，强制使用比较的方法以定义明确的方式失败。

## <a name="see-also"></a>另请参阅

[CSimpleMapEqualHelper 类](../../atl/reference/csimplemapequalhelper-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
