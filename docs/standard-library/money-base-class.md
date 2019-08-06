---
title: money_base 类
ms.date: 11/04/2016
f1_keywords:
- xlocmon/std::money_base
helpviewer_keywords:
- money_base class
ms.assetid: 1a303c15-9272-4f26-ae16-dcf43a0fd38a
ms.openlocfilehash: 5b19635cf4d2cce58ec50226c463a075cfac5b0f
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68455567"
---
# <a name="moneybase-class"></a>money_base 类

此类会描述常用于所有模板类 [moneypunct](../standard-library/moneypunct-class.md) 专用化的枚举和结构。

## <a name="syntax"></a>语法

```cpp
struct pattern
{
   char field[_PATTERN_FIELD_SIZE];
};
```

## <a name="remarks"></a>备注

枚举`part`描述结构模式中数组字段的元素中的可能值。 的`part`值为:

- `none`匹配零个或多个空格, 或不生成任何内容。

- `sign`匹配或生成正号或负号。

- `space`匹配零个或多个空格或生成空格。

- `symbol`匹配或生成货币符号。

- `value`若要匹配或生成货币值, 则为。

## <a name="requirements"></a>要求

**标头：** \<locale>

**命名空间：** std

## <a name="see-also"></a>请参阅

[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
