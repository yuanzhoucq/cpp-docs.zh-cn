---
title: hdrstop |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- hdrstop_CPP
- vc-pragma.hdrstop
dev_langs:
- C++
helpviewer_keywords:
- hdrstop pragma
- pragmas, hdrstop
ms.assetid: 5ea8370a-10d1-4538-ade6-4c841185da0e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0e571229602a311633fc7425384544c53813b935
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50059709"
---
# <a name="hdrstop"></a>hdrstop
提供对预编译文件名和编译状态的保存位置的额外控制。

## <a name="syntax"></a>语法

```
#pragma hdrstop [( "filename" )]
```

## <a name="remarks"></a>备注

*文件名*是要使用或创建的预编译标头文件的名称 (具体取决于是否[/Yu](../build/reference/yu-use-precompiled-header-file.md)或[/Yc](../build/reference/yc-create-precompiled-header-file.md)指定)。 如果*文件名*不包含路径说明，预编译的头文件被假定为与源文件相同的目录中。

如果 C 或 c + + 文件包含**hdrstop**杂注编译时使用`/Yc`，则编译器将保存到的位置的杂注在编译的状态。 不会保存遵循杂注的任何代码的编译状态。

使用*文件名*命名预编译标头文件在其中保存编译的状态。 之间有空格**hdrstop**并*filename*是可选的。 中指定的文件名称**hdrstop**杂注是一个字符串，因此会受到任何 C 或 c + + 字符串的约束。 具体来说，您必须将其包含在引号中并使用转义符（反斜杠）来指定目录名称。 例如：

```
#pragma hdrstop( "c:\\projects\\include\\myinc.pch" )
```

预编译标头文件的名称是根据以下规则按优先顺序决定的。

1. 参数`/Fp`编译器选项

2. *文件名*参数 `#pragma hdrstop`

3. 扩展名为 .PCH 的源文件基名称

有关`/Yc`并`/Yu`选项，如果这两个编译选项也不**hdrstop**杂注指定的文件名称、 源文件的基名称用作预编译的头文件的基名称。

还可以使用预处理命令来执行宏替换，如下所示：

```
#define INCLUDE_PATH "c:\\progra~`1\\devstsu~1\\vc\\include\\"
#define PCH_FNAME "PROG.PCH"
.
.
.
#pragma hdrstop( INCLUDE_PATH PCH_FNAME )
```

以下规则控制在何处**hdrstop**可以放置杂注：

- 它必须出现在任何数据或函数声明/定义的外部。

- 必须在源文件而不是头文件中指定它。

## <a name="example"></a>示例

```
#include <windows.h>                 // Include several files
#include "myhdr.h"

__inline Disp( char *szToDisplay )   // Define an inline function
{
    ...                              // Some code to display string
}
#pragma hdrstop
```

在此示例中， **hdrstop**杂注显示后包含了两个文件和已定义内联函数。 最初，这可能是杂注的临时位置。 请考虑，但是，使用手动预编译选项，`/Yc`并`/Yu`，使用**hdrstop**杂注使你可以预编译整个源文件-甚至是内联代码。 Microsoft 编译器不会只允许您预编译数据声明。

## <a name="see-also"></a>请参阅

[Pragma 指令和 __Pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)