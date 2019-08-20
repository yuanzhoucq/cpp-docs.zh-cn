---
title: nullopt_t 结构
ms.date: 08/04/2019
f1_keywords:
- optional/std::nullopt_t
- optional/std::nullopt
ms.openlocfilehash: 1f453a5d75de3f6dedb133d55c094a4f4274e08f
ms.sourcegitcommit: 16c0392fc8d96e814c3a40b0c5346d7389aeb525
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/12/2019
ms.locfileid: "68957048"
---
# <a name="nullopt_t-struct"></a>nullopt_t 结构

类型是唯一的空类型, 用于指示[可选](optional-class.md)对象不包含值。  `nullopt_t`

类型`nullopt` `optional`的常量指示类型的状态为未初始化。 `nullopt_t` 它可用于初始化`optional`对象或与一个对象进行比较。

## <a name="syntax"></a>语法

```cpp
struct nullopt_t;
inline constexpr nullopt_t nullopt{ /*implementation-defined*/ };
```

## <a name="see-also"></a>请参阅

[\<可选 >](optional.md)\
[可选类](optional-class.md)
