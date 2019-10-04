---
title: '#undef 指令 (C/C++)'
ms.date: 08/29/2019
f1_keywords:
- '#undef'
helpviewer_keywords:
- '#undef directive'
- undef directive (#undef)
- preprocessor, directives
ms.assetid: 88900e0e-2c19-4a63-b681-f3d3133c24ca
ms.openlocfilehash: 1a69bc568579e7da7c7e3816cb67c8153b8f1a27
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220213"
---
# <a name="undef-directive-cc"></a>#undef 指令 (C/C++)

移除（取消定义）之前使用 `#define` 创建的名称。

## <a name="syntax"></a>语法

> **#undef** *标识符*

## <a name="remarks"></a>备注

**#Undef**指令删除当前的*标识符*定义。 因此, 预处理器将忽略以后出现的*标识符*。 若要使用 **#undef**删除宏定义, 请仅指定宏*标识符*, 而不是参数列表。

还可以将 **#undef**指令应用于没有先前定义的标识符。 这将确保该标识符是不确定的。 不在 **#undef**语句内执行宏替换。

**#Undef**指令通常与`#define`指令配对, 以在源程序中创建区域, 其中标识符具有特殊意义。 例如，源程序的特定函数可使用清单常量定义不会影响程序的其余部分的环境特定值。 **#Undef**指令还适用`#if`于控制源程序的条件编译的指令。 有关详细信息, 请参阅[#if、#elif、#else 和 #endif 指令](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)。

在下面的示例中, **#undef**指令删除符号常量和宏的定义。 请注意，只给定宏的标识符。

```C
#define WIDTH 80
#define ADD( X, Y ) ((X) + (Y))
.
.
.
#undef WIDTH
#undef ADD
```

**Microsoft 专用**

宏可以从命令行中使用`/U`选项进行定义, 后跟要定义的宏名称。 发出此命令的效果等效于文件开头的`#undef` *宏名*语句序列。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[预处理器指令](../preprocessor/preprocessor-directives.md)
