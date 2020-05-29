---
title: CompareStringOrdinal 方法
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::CompareStringOrdinal
ms.assetid: ffa997fd-8cd7-40a5-b9e7-f55d40b072f4
ms.openlocfilehash: 1291084395b02602b7a3de9013df6720d2e237fc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214092"
---
# <a name="comparestringordinal-method"></a>CompareStringOrdinal 方法

支持 WRL 基础结构，不应在代码中直接使用。

## <a name="syntax"></a>语法

```cpp
inline INT32 CompareStringOrdinal(
   HSTRING lhs,
   HSTRING rhs)
```

### <a name="parameters"></a>parameters

*lhs*<br/>
要比较的第一个 HSTRING。

rhs<br/>
要比较的第二个 HSTRING。

## <a name="return-value"></a>返回值

|值|条件|
|-----------|---------------|
|-1|*lhs*小于*rhs*。|
|0|*lhs*等于*rhs*。|
|1|*lhs*大于*rhs*。|

## <a name="remarks"></a>备注

比较两个指定的 HSTRING 对象，并返回一个指示二者在排序顺序中的相对位置的整数。

## <a name="requirements"></a>要求

**标头：** corewrappers。h

**命名空间：** Microsoft：： WRL：：包装：:D etails

## <a name="see-also"></a>另请参阅

[Microsoft::WRL::Wrappers::Details 命名空间](microsoft-wrl-wrappers-details-namespace.md)
