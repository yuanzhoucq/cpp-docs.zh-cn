---
title: 定义 NMAKE 宏
ms.date: 11/04/2016
helpviewer_keywords:
- macros, NMAKE
- defining NMAKE macros
- NMAKE macros, defining
ms.assetid: 45aae451-9d33-4a3d-8799-2e0cae17070d
ms.openlocfilehash: 860a5766e0d766f7426cb6c1a7eaf5db02686aa4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50498967"
---
# <a name="defining-an-nmake-macro"></a>定义 NMAKE 宏

## <a name="syntax"></a>语法

```

macroname=string
```

## <a name="remarks"></a>备注

*Macroname*是字母、 数字和下划线 (_) 最多 1,024 个字符的组合，并且是敏感的情况。 *Macroname*可以包含被调用的宏。 如果*macroname*包括完全由被调用的宏，宏调用不能为 null 或未定义。

`string`可以是零个或多个字符的任何序列。 Null 字符串包含零个字符或仅空格或制表符。 `string`可以包含宏调用。

## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？

[宏内的特殊字符](../build/special-characters-in-macros.md)

[Null 宏和未定义宏](../build/null-and-undefined-macros.md)

[定义宏的位置](../build/where-to-define-macros.md)

[宏定义中的优先级](../build/precedence-in-macro-definitions.md)

## <a name="see-also"></a>请参阅

[宏和 NMAKE](../build/macros-and-nmake.md)