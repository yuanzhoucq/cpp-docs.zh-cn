---
title: include_alias 杂注
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.include_alias
- include_alias_CPP
helpviewer_keywords:
- pragmas, include_alias
- include_alias pragma
ms.assetid: 3256d589-12b3-4af0-a586-199e96eabacc
ms.openlocfilehash: aa3714186e8f95d4044ba5a3b2bc2d5fcfb1fc9c
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218900"
---
# <a name="include_alias-pragma"></a>include_alias 杂注

指定在`#include`指令中找到*alias_filename*时, 编译器会在其位置替换*actual_filename* 。

## <a name="syntax"></a>语法

<!-- localization note - it's important to have the italic and bold characters immediately adjacent here. -->
> **#pragma include_alias (** "*alias_filename*" **,** "*actual_filename*" **)** \
> **#pragma include_alias (** \< *alias_filename*>  **,** *actual_filename*) \<> 

## <a name="remarks"></a>备注

**Include_alias** pragma 指令允许用不同的名称或路径替换源文件中包含的文件名。 例如, 某些文件系统允许超过 8.3 FAT 文件系统限制的标头文件名。 编译器不能将更长的名称截断到 8.3, 因为较长的标头文件名的前八个字符可能不是唯一的。 每当编译器发现`#include`指令中的*alias_filename*字符串时, 它会改为替换*actual_filename*名称。 然后, 它加载*actual_filename*头文件。 此杂注必须在相应的 `#include` 指令之前出现。 例如:

```cpp
// First eight characters of these two files not unique.
#pragma include_alias( "AppleSystemHeaderQuickdraw.h", "quickdra.h" )
#pragma include_alias( "AppleSystemHeaderFruit.h", "fruit.h" )

#pragma include_alias( "GraphicsMenu.h", "gramenu.h" )

#include "AppleSystemHeaderQuickdraw.h"
#include "AppleSystemHeaderFruit.h"
#include "GraphicsMenu.h"
```

要搜索的别名必须与规范完全匹配。 用双引号或尖括号括起来的情况必须全部匹配。 **Include_alias**杂注对文件名执行简单的字符串匹配。 不执行其他文件名验证。 例如，给定下列指令，

```cpp
#pragma include_alias("mymath.h", "math.h")
#include "./mymath.h"
#include "sys/mymath.h"
```

由于标头文件字符串不完全匹配, 因此不执行任何别名替换。 此外, 用作`/Yu`和`/Yc`编译器选项的参数的标头文件名或杂注不会被替换。`hdrstop` 例如，如果源文件包含以下指令，

```cpp
#include <AppleSystemHeaderStop.h>
```

则相应的编译器选项应为

> **/YcAppleSystemHeaderStop.h**

您可以使用**include_alias**杂注将任何标头文件名映射到另一个。 例如:

```cpp
#pragma include_alias( "api.h", "c:\version1.0\api.h" )
#pragma include_alias( <stdio.h>, <newstdio.h> )
#include "api.h"
#include <stdio.h>
```

不要混合用双引号引起来的文件名括在尖括号中。 例如, 在给定上述两个`#pragma include_alias`指令的情况下, 编译器不会对以下`#include`指令进行替换:

```cpp
#include <api.h>
#include "stdio.h"
```

而且，以下指令将生成错误：

```cpp
#pragma include_alias(<header.h>, "header.h")  // Error
```

错误消息中报告的文件名或预定义`__FILE__`的宏的值是完成替换后的文件名称。 有关示例, 请参阅以下指令后面的输出:

```cpp
#pragma include_alias( "VERYLONGFILENAME.H", "myfile.h" )
#include "VERYLONGFILENAME.H"
```

VERYLONGFILENAME 中的错误 *。H*产生以下错误消息:

```Output
myfile.h(15) : error C2059 : syntax error
```

另请注意, 不支持传递性。 给定以下指令，

```cpp
#pragma include_alias( "one.h", "two.h" )
#pragma include_alias( "two.h", "three.h" )
#include "one.h"
```

编译器会搜索文件*两个 .h* , 而不是*三个 .h*。

## <a name="see-also"></a>请参阅

[Pragma 指令和 __pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
