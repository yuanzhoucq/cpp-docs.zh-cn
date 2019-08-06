---
title: independent_bits_engine 类
ms.date: 11/04/2016
f1_keywords:
- random/std::independent_bits_engine
helpviewer_keywords:
- independent_bits_engine class
ms.assetid: 889e9a82-f457-49a7-9d2e-26e0fc3cd907
ms.openlocfilehash: a90e4be4ff6e92734f6b2e6804f8059be78e66b9
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456345"
---
# <a name="independentbitsengine-class"></a>independent_bits_engine 类

通过再次从其基引擎返回的值中打包位，生成具有指定位数的随机数字序列。

## <a name="syntax"></a>语法

```cpp
template <class Engine, size_t W, class UIntType>
class independent_bits_engine;
```

### <a name="parameters"></a>参数

*搜索引擎优化*\
基引擎类型。

*水平*\
**字大小**。 生成的每个数字的大小（以字节为单位）。 **前提条件**：`0 < W ≤ numeric_limits<UIntType>::digits`

*UIntType*\
无符号的整数结果类型。 有关可能的类型，请参阅 [\<random>](../standard-library/random.md)。

## <a name="members"></a>成员

||||
|-|-|-|
|`independent_bits_engine::independent_bits_engine`|`independent_bits_engine::base`|`independent_bits_engine::discard`|
|`independent_bits_engine::operator()`|`independent_bits_engine::base_type`|`independent_bits_engine::seed`|

有关引擎成员的详细信息，请参阅 [\<random>](../standard-library/random.md)。

## <a name="remarks"></a>备注

此模板类描述了一个*引擎适配器*, 该适配器通过从其基引擎返回的值中重新打包位来生成值, 从而产生*W*位值。

## <a name="requirements"></a>要求

**标头：** \<random>

**命名空间：** std

## <a name="see-also"></a>请参阅

[\<random>](../standard-library/random.md)
