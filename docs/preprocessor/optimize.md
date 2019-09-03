---
title: optimize 杂注
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.optimize
- optimize_CPP
helpviewer_keywords:
- pragmas, optimize
- optimize pragma
ms.assetid: cb13c1cc-186a-45bc-bee7-95a8de7381cc
ms.openlocfilehash: 6d7b99b7a72c133d56a209cf42fa9ef670a4a7f9
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220515"
---
# <a name="optimize-pragma"></a>optimize 杂注

指定逐函数的优化。

## <a name="syntax"></a>语法

> **#pragma optimize ("** [*优化-list* ] **",** { **on** | **off** } **)**

## <a name="remarks"></a>备注

**优化**杂注必须出现在函数之外。 它在显示杂注后定义的第一个函数处生效。 On和**off**参数打开或关闭*优化列表*中指定的选项。

*优化列表*可以是下表中显示的零个或多个参数。

### <a name="parameters-of-the-optimize-pragma"></a>optimize 杂注的参数

| 参数 | 优化的类型 |
|--------------------|--------------------------|
| **g** | 启用全局优化。 |
| **s**或**t** | 指定机器代码的短或快速序列。 |
| **y** | 在程序堆栈上生成帧指针。 |

这些参数与[/o](../build/reference/o-options-optimize-code.md)编译器选项一起使用的字符相同。 例如，以下杂注等效于 `/Os` 编译器选项：

```cpp
#pragma optimize( "s", on )
```

将**optimize**杂注与空字符串 ( **""** ) 结合使用是该指令的特殊形式:

当使用**off**参数时, 它会关闭所有优化、 **g**、 **s**、 **t**和**y**。

当你使用**on**参数时, 它会将优化重置为你使用[/o](../build/reference/o-options-optimize-code.md)编译器选项指定的优化。

```cpp
#pragma optimize( "", off )
/* unoptimized code section */
#pragma optimize( "", on )
```

## <a name="see-also"></a>请参阅

[Pragma 指令和 __pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
