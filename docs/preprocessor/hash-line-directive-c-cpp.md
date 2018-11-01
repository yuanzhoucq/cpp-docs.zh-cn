---
title: '#行指令 （C/c + +）'
ms.date: 10/18/2017
f1_keywords:
- '#line'
helpviewer_keywords:
- preprocessor, directives
- line directive (#line)
- '#line directive'
ms.assetid: 585c1dc4-5184-4f01-98f4-80c1909744d7
ms.openlocfilehash: e478d287af097081910d192e2ac0fbee6890bfa2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50614755"
---
# <a name="line-directive-cc"></a>#line 指令 (C/C++)

**#Line**指令告知预处理器的编译器在内部存储的行号和文件名更改为给定的行号和文件名。

## <a name="syntax"></a>语法

> **#line** *digit-sequence* ["*filename*"]

## <a name="remarks"></a>备注

编译器使用的行号和可选的文件名来指代在编译过程中发现的错误。 行号通常是指当前的输入行和文件名指的是当前的输入文件。 处理每行后，就会增加的行号。

*数字序列*值可以是任何整数常量。 可对预处理标记中，执行宏替换，但结果的计算结果必须为正确的语法。 *文件名*可以是字符的任意组合并且必须括在双引号引起来 (**""**)。 如果*文件名*是省略，以前的文件名将保持不变。

您可以通过编写修改的源行号和文件名 **#line**指令。 翻译人员使用的行号和文件名来确定值的预定义的宏`__FILE__`和`__LINE__`。 这些宏可用于将自我描述的错误消息插入到的程序文本。 有关这些预定义的宏的详细信息，请参阅[预定义的宏](../preprocessor/predefined-macros.md)。

`__FILE__`宏扩展为一个字符串，其内容是由双引号括起来的文件名 (**""**)。

如果您更改的行号和文件名，编译器将忽略以前的值，并将继续处理新值。 **#Line**指令通常用于由程序生成器会导致错误消息来指代的原始源文件而不是生成程序。

以下示例说明了 **#line**并`__LINE__`和`__FILE__`宏。

在此语句中，在内部存储的行号设置为 151 和文件名更改为 copy.c。

```cpp
#line 151 "copy.c"
```

在此示例中，该宏`ASSERT`使用预定义的宏`__LINE__`和`__FILE__`打印有关的源文件的错误消息，如果给定的断言不为 true。

```cpp
#define ASSERT(cond) if( !(cond) )\
{printf( "assertion error line %d, file(%s)\n", \
__LINE__, __FILE__ );}
```

## <a name="see-also"></a>请参阅

[预处理器指令](../preprocessor/preprocessor-directives.md)