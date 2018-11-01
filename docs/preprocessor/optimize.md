---
title: optimize
ms.date: 11/04/2016
f1_keywords:
- vc-pragma.optimize
- optimize_CPP
helpviewer_keywords:
- pragmas, optimize
- optimize pragma
ms.assetid: cb13c1cc-186a-45bc-bee7-95a8de7381cc
ms.openlocfilehash: 65948f2b466bdd40bd753dbba99e2e235c57b0f6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50615860"
---
# <a name="optimize"></a>optimize

指定要对每个函数执行的优化。

## <a name="syntax"></a>语法

```
#pragma optimize( "[optimization-list]", {on | off} )
```

## <a name="remarks"></a>备注

**优化**杂注必须出现在函数的外部，并定义杂注后的第一个函数处生效。 *上*并*off*参数打开选项中指定*优化列表*打开或关闭。

*优化列表*可以是零个或多个表所示的参数。

### <a name="parameters-of-the-optimize-pragma"></a>optimize 杂注的参数

|参数|优化的类型|
|--------------------|--------------------------|
|*g*|启用全局优化。|
|*s*或*t*|指定机器代码的短或快速序列。|
|*y*|在程序堆栈上生成帧指针。|

这些是与一起使用的相同字母[/O](../build/reference/o-options-optimize-code.md)编译器选项。 例如，以下杂注等效于 `/Os` 编译器选项：

```
#pragma optimize( "ts", on )
```

使用**优化**杂注和空字符串 (**""**) 是指令的特殊形式：

当你使用*关闭*参数，它将所有的优化*g*， *s*， *t*，和*y*、 off。

当你使用*上*参数，它会重置优化为使用指定的[/O](../build/reference/o-options-optimize-code.md)编译器选项。

```
#pragma optimize( "", off )
.
.
.
#pragma optimize( "", on )
```

## <a name="see-also"></a>请参阅

[Pragma 指令和 __Pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)