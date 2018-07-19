---
title: independent_bits_engine 类 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- random/std::independent_bits_engine
dev_langs:
- C++
helpviewer_keywords:
- independent_bits_engine class
ms.assetid: 889e9a82-f457-49a7-9d2e-26e0fc3cd907
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f802dc91c3429ba718778d122d1a787aad0dec87
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/11/2018
ms.locfileid: "38964218"
---
# <a name="independentbitsengine-class"></a>independent_bits_engine 类

通过再次从其基引擎返回的值中打包位，生成具有指定位数的随机数字序列。

## <a name="syntax"></a>语法

```cpp
template <class Engine, size_t W, class UIntType>
class independent_bits_engine;
```

### <a name="parameters"></a>参数

*引擎*基引擎类型。

*W* **字大小**。 生成的每个数字的大小（以字节为单位）。 **前提条件**：`0 < W ≤ numeric_limits<UIntType>::digits`

*UIntType*无符号的整数结果类型。 有关可能的类型，请参阅 [\<random>](../standard-library/random.md)。

## <a name="members"></a>成员

||||
|-|-|-|
|`independent_bits_engine::independent_bits_engine`|`independent_bits_engine::base`|`independent_bits_engine::discard`|
|`independent_bits_engine::operator()`|`independent_bits_engine::base_type`|`independent_bits_engine::seed`|

有关引擎成员的详细信息，请参阅 [\<random>](../standard-library/random.md)。

## <a name="remarks"></a>备注

此模板类描述*引擎适配器*通过再次打包其基引擎，从而导致返回的值中的位来产生值*W*-位的值。

## <a name="requirements"></a>要求

**标头：**\<random>

**命名空间：** std

## <a name="see-also"></a>请参阅

[\<random>](../standard-library/random.md)<br/>
