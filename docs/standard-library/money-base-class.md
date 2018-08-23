---
title: money_base 类 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- xlocmon/std::money_base
dev_langs:
- C++
helpviewer_keywords:
- money_base class
ms.assetid: 1a303c15-9272-4f26-ae16-dcf43a0fd38a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3195d2c988abcfb2d62acb4ece957c8c5156bbd7
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/11/2018
ms.locfileid: "38965683"
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

枚举`part`描述结构模式中数组字段的元素中的可能值。 值`part`是：

- `none` 若要匹配零个或多个空格，或不生成任何内容。

- `sign` 用于匹配或生成正负号。

- `space` 用于匹配零个或多个空格，或生成空格。

- `symbol` 用于匹配或生成货币符号。

- `value` 用于匹配或生成货币值。

## <a name="requirements"></a>要求

**标头：** \<locale>

**命名空间：** std

## <a name="see-also"></a>请参阅

[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
