---
title: CompareStringOrdinal 方法
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::CompareStringOrdinal
ms.assetid: ffa997fd-8cd7-40a5-b9e7-f55d40b072f4
ms.openlocfilehash: a1ac0576bdd374daa5cbd445af480e7652b61e45
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59027698"
---
# <a name="comparestringordinal-method"></a>CompareStringOrdinal 方法

支持 WRL 基础结构，不应在代码中直接使用。

## <a name="syntax"></a>语法

```cpp
inline INT32 CompareStringOrdinal(
   HSTRING lhs,
   HSTRING rhs)
```

### <a name="parameters"></a>参数

*lhs*<br/>
第一个要比较的 HSTRING。

*rhs*<br/>
要比较的第二个 HSTRING。

## <a name="return-value"></a>返回值

|“值”|条件|
|-----------|---------------|
|-1|*lhs*是小于*rhs*。|
|0|*lhs*等于*rhs*。|
|1|*lhs*大于*rhs*。|

## <a name="remarks"></a>备注

比较两个指定的 HSTRING 对象并返回一个整数，指示二者在排序顺序中的相对位置。

## <a name="requirements"></a>要求

**标头：** corewrappers.h

**命名空间：** Microsoft::WRL::Wrappers::Details

## <a name="see-also"></a>请参阅

[Microsoft::WRL::Wrappers::Details 命名空间](microsoft-wrl-wrappers-details-namespace.md)