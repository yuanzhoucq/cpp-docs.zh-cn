---
title: '#line 指令 (C/C++)'
ms.date: 08/29/2019
f1_keywords:
- '#line'
helpviewer_keywords:
- preprocessor, directives
- line directive (#line)
- '#line directive'
ms.assetid: 585c1dc4-5184-4f01-98f4-80c1909744d7
ms.openlocfilehash: 35bee779ebf059c20d4a46e27b5ad4cbfb3ce5f3
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220223"
---
# <a name="line-directive-cc"></a>#line 指令 (C/C++)

**#Line**指令指示预处理器将编译器内部存储的行号和文件名更改为给定的行号和文件名。

## <a name="syntax"></a>语法

> **#line** *digit-sequence* ["*filename*"]

## <a name="remarks"></a>备注

编译器使用行号和可选文件名来引用它在编译过程中发现的错误。 行号通常指的是当前输入行, filename 指的是当前输入文件。 每行处理一次后, 行号就会增加。

*数字序列*值可以是任何整数常量。 可以对预处理标记执行宏替换, 但结果的计算结果必须为正确的语法。 *文件名*可以是字符的任意组合, 必须用双引号 (`" "`) 引起来。 如果省略*filename* , 则前一个文件名保持不变。

可以通过编写 **#line**指令来更改源行号和文件名。 转换器使用行号和文件名来确定预定义宏`__FILE__`和`__LINE__`的值。 您可以使用这些宏将自描述错误消息插入程序文本中。 有关这些预定义的宏的详细信息, 请参阅[预定义的宏](../preprocessor/predefined-macros.md)。

宏将扩展为其内容为文件名的字符串, 并将其括在双引号 (`" "`) 中。 `__FILE__`

如果更改行号和文件名, 编译器将忽略以前的值并继续处理新值。 程序生成器通常使用 **#line**指令来导致错误消息引用原始源文件而不是生成的程序。

下面的示例演示 **#line**和`__LINE__`和`__FILE__`宏。

在此语句中, 将内部存储的行号设置为 151, 并将文件名更改为. c。

```C
#line 151 "copy.c"
```

在此示例中, 当`ASSERT`给定的断言不`__LINE__`为`__FILE__` true 时, 宏将使用预定义的宏, 并打印有关源文件的错误消息。

```C
#define ASSERT(cond) if( !(cond) )\
{printf( "assertion error line %d, file(%s)\n", \
__LINE__, __FILE__ );}
```

## <a name="see-also"></a>请参阅

[预处理器指令](../preprocessor/preprocessor-directives.md)
