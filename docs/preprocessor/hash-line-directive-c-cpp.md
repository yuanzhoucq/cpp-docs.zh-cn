---
title: "#<a name=\"line-directive-cc--microsoft-docs\"></a>行指令 （C/c + +） |Microsoft 文档"
ms.custom: 
ms.date: 10/18/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: '#line'
dev_langs: C++
helpviewer_keywords:
- preprocessor, directives
- line directive (#line)
- '#line directive'
ms.assetid: 585c1dc4-5184-4f01-98f4-80c1909744d7
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 41886c8107db882ad3bea5a041b529ba8bbbeed6
ms.sourcegitcommit: ca2f94dfd015e0098a6eaf5c793ec532f1c97de1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="line-directive-cc"></a>#line 指令 (C/C++)

`#line`指令告知预处理器将编译器的内部存储的行号和文件名更改为给定的行号和文件名。

## <a name="syntax"></a>语法

> **#line** *数字序列*["*filename*"]

## <a name="remarks"></a>备注

编译器使用的行号和可选的文件名来引用在编译过程中发现的错误。 行号通常是指当前的输入行和文件名引用当前的输入文件。 处理每个行后，即会递增的行号。

*数字序列*该值可以为任何整数常量。 可以对预处理标记中，执行宏替换，但结果的计算结果必须为正确的语法。 *Filename*可以是字符的任意组合，并且必须括在双引号 (**""**)。 如果*filename*是省略，以前的文件名保持不变。

你可以更改在源代码行号和 filename 通过编写`#line`指令。 转换器使用的行号和文件名来确定的预定义的宏的值**&#95; &#95;文件 &#95; &#95;**和**&#95; &#95;行 &#95; &#95;**. 这些宏可用于自我描述的错误消息插入的程序文本。 这些预定义的宏的详细信息，请参阅[预定义宏](../preprocessor/predefined-macros.md)。

**&#95; &#95;文件 &#95; &#95;**宏扩展为一个字符串，其内容是由双引号括起来的文件名 (**""**)。

如果你更改的行号和文件名，编译器将忽略以前的值，并且将继续处理的新值。 `#line`指令通常用于通过程序生成器导致错误消息来引用的原始源文件而不是生成程序。

下面的示例阐释`#line`和**&#95; &#95;行 &#95; &#95;**和**&#95; &#95;文件 &#95; &#95;**宏。

在此语句中，内部存储的行号设置为 151 和文件名更改为 copy.c。

```cpp
#line 151 "copy.c"
```

 在此示例中，宏`ASSERT`使用预定义的宏**&#95; &#95;行 &#95; &#95;**和**&#95; &#95;文件 &#95; &#95;**以打印有关的源文件的错误消息，如果给定的断言不为 true。

```cpp
#define ASSERT(cond) if( !(cond) )\
{printf( "assertion error line %d, file(%s)\n", \
__LINE__, __FILE__ );}
```

## <a name="see-also"></a>另请参阅

[预处理器指令](../preprocessor/preprocessor-directives.md)