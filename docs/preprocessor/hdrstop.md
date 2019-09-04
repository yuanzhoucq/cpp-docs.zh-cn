---
title: hdrstop 杂注
ms.date: 08/29/2019
f1_keywords:
- hdrstop_CPP
- vc-pragma.hdrstop
helpviewer_keywords:
- hdrstop pragma
- pragmas, hdrstop
ms.assetid: 5ea8370a-10d1-4538-ade6-4c841185da0e
ms.openlocfilehash: f540f0f01fe654213af15afa8fbf5cbd94e4b7e2
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221016"
---
# <a name="hdrstop-pragma"></a>hdrstop 杂注

向您提供对预编译文件名称以及编译状态保存位置的额外控制。

## <a name="syntax"></a>语法

> **#pragma hdrstop**[("*文件名*")]

## <a name="remarks"></a>备注

*Filename*是要使用或创建的预编译头文件的名称 (取决于是否指定了[/yu](../build/reference/yu-use-precompiled-header-file.md)或[/yc](../build/reference/yc-create-precompiled-header-file.md) )。 如果*filename*不包含路径规范, 则假定预编译标头文件位于源文件所在的同一目录中。

如果 C 或C++文件包含使用进行编译时使用`/Yc`的 hdrstop 杂注, 则编译器会将编译状态保存到杂注的位置。 不保存遵循杂注的任何代码的编译状态。

使用*filename*来命名已编译状态保存到的预编译头文件。 **Hdrstop**和*filename*之间的空格是可选的。 **Hdrstop**杂注中指定的文件名是字符串, 因此受限于任何 C 或C++字符串的约束。 具体来说，您必须将其包含在引号中并使用转义符（反斜杠）来指定目录名称。 例如:

```C
#pragma hdrstop( "c:\\projects\\include\\myinc.pch" )
```

预编译标头文件的名称是根据以下规则按优先顺序决定的。

1. `/Fp`编译器选项的参数

2. *Filename*参数`#pragma hdrstop`

3. 扩展名为 .PCH 的源文件基名称

`/Yc`对于和`/Yu`选项, 如果两个编译选项和**hdrstop**杂注都不指定文件名, 则将源文件的基名称用作预编译标头文件的基名称。

还可以使用预处理命令来执行宏替换，如下所示：

```C
#define INCLUDE_PATH "c:\\progra~`1\\devstsu~1\\vc\\include\\"
#define PCH_FNAME "PROG.PCH"
.
.
.
#pragma hdrstop( INCLUDE_PATH PCH_FNAME )
```

以下规则控制**hdrstop**杂注的放置位置:

- 它必须出现在任何数据或函数声明/定义的外部。

- 必须在源文件而不是头文件中指定它。

## <a name="example"></a>示例

```C
#include <windows.h>                 // Include several files
#include "myhdr.h"

__inline Disp( char *szToDisplay )   // Define an inline function
{
    // ...                           // Some code to display string
}
#pragma hdrstop
```

在此示例中, **hdrstop**杂注显示了两个文件, 并定义了一个内联函数。 对于杂注, 此位置可能在第一位置看来是奇数位置。 不过, 请考虑使用手动预编译选项, `/Yc` `/Yu`使用**hdrstop**杂注, 可以预编译整个源文件-甚至是内联代码。 Microsoft 编译器不会只允许您预编译数据声明。

## <a name="see-also"></a>请参阅

[Pragma 指令和 __pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
