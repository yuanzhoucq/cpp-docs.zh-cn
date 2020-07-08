---
title: '#line 指令 (C/C++)'
description: '描述 #line 指令，该指令用于设置预处理器宏报告的行号和文件名。'
ms.date: 07/06/2020
f1_keywords:
- '#line'
helpviewer_keywords:
- preprocessor, directives
- line directive (#line)
- '#line directive'
ms.assetid: 585c1dc4-5184-4f01-98f4-80c1909744d7
ms.openlocfilehash: 7b671cfdf5d5ce43024ac3e038c214396ac8679c
ms.sourcegitcommit: 85d96eeb1ce41d9e1dea947f65ded672e146238b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/07/2020
ms.locfileid: "86058615"
---
# <a name="line-directive-cc"></a>#line 指令（C/c + +）

**#Line**指令指示预处理器将行号和文件名的编译器报告值设置为给定的行号和文件名。

## <a name="syntax"></a>语法

> **`#line`***数字序列*["*filename*"]

## <a name="remarks"></a>备注

编译器使用行号和可选文件名来引用它在编译过程中发现的错误。 行号通常指的是当前输入行，filename 指的是当前输入文件。 每行处理一次后，行号就会增加。

*数字序列*值可以是任何整数常量。 可以对预处理标记使用宏替换，但结果的计算结果必须为正确的语法。 *文件名*可以是字符的任意组合，必须用双引号（）引起来 `" "` 。 如果省略*filename* ，则前一个文件名保持不变。

可以通过编写指令来更改源行号和文件名 **`#line`** 。 **`#line`** 指令设置紧跟在源文件中的指令后面的行的值。 转换器使用行号和文件名来确定预定义宏和的值 `__FILE__` `__LINE__` 。 您可以使用这些宏将自描述错误消息插入程序文本中。 有关这些预定义的宏的详细信息，请参阅[预定义的宏](../preprocessor/predefined-macros.md)。

`__FILE__`宏将扩展为其内容为文件名的字符串，并将其括在双引号（ `" "` ）中。

如果更改行号和文件名，编译器将忽略以前的值并继续处理新值。 **#Line**指令通常由程序生成器使用。 它用于使错误消息引用原始源文件，而不是所生成的程序。

## <a name="example"></a>示例

下面的示例阐释 **`#line`** 了和 `__LINE__` 和 `__FILE__` 宏。

在第一个示例中，行号设置为10，然后设置为20，文件名更改为 " *hello*"。

```cpp
// line_directive.cpp
// Compile by using: cl /W4 /EHsc line_directive.cpp
#include <stdio.h>

int main()
{
    printf( "This code is on line %d, in file %s\n", __LINE__, __FILE__ );
#line 10
    printf( "This code is on line %d, in file %s\n", __LINE__, __FILE__ );
#line 20 "hello.cpp"
    printf( "This code is on line %d, in file %s\n", __LINE__, __FILE__ );
    printf( "This code is on line %d, in file %s\n", __LINE__, __FILE__ );
}
```

```Output
This code is on line 7, in file line_directive.cpp
This code is on line 10, in file line_directive.cpp
This code is on line 20, in file hello.cpp
This code is on line 21, in file hello.cpp
```

在此示例中， `ASSERT` `__LINE__` 当给定的断言不为 true 时，宏将使用预定义的宏，并 `__FILE__` 打印有关源文件的错误消息。

```C
#define ASSERT(cond) if( !(cond) )\
{printf( "assertion error line %d, file(%s)\n", \
__LINE__, __FILE__ );}
```

## <a name="see-also"></a>另请参阅

[预处理器指令](../preprocessor/preprocessor-directives.md)
