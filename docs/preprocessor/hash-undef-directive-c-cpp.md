---
title: '#undef 指令 （C/c + +）'
ms.date: 11/04/2016
f1_keywords:
- '#undef'
helpviewer_keywords:
- '#undef directive'
- undef directive (#undef)
- preprocessor, directives
ms.assetid: 88900e0e-2c19-4a63-b681-f3d3133c24ca
ms.openlocfilehash: 4f4f5ce244be6d7f4e13d7a2abc5d21232c08d9d
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "59039002"
---
# <a name="undef-directive-cc"></a>#undef 指令 (C/C++)
移除（取消定义）之前使用 `#define` 创建的名称。

## <a name="syntax"></a>语法

```
#undef
identifier
```

## <a name="remarks"></a>备注

**#Undef**指令将删除当前定义的*标识符*。 因此的后续匹配项*标识符*由预处理器忽略。 若要删除宏定义使用 **#undef**，仅给定宏*标识符*; 但不会给参数列表。

您还可以应用 **#undef**指令之前没有定义的标识符。 这将确保该标识符是不确定的。 中不执行宏替换 **#undef**语句。

**#Undef**指令通常与配对`#define`指令在其中一个标识符具有特殊含义的源程序中创建一个区域。 例如，源程序的特定函数可使用清单常量定义不会影响程序的其余部分的环境特定值。 **#Undef**指令还适用于`#if`指令来控制源程序的条件编译。 请参阅[#if、 #elif，#else 和 #endif 指令](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)有关详细信息。

在以下示例中， **#undef**指令将移除符号常量和宏的定义。 请注意，只给定宏的标识符。

```
#define WIDTH 80
#define ADD( X, Y ) ((X) + (Y))
.
.
.
#undef WIDTH
#undef ADD
```

**Microsoft 专用**

可以是从命令行中使用未定义的宏`/U`选项后跟要是未定义的宏名称。 发出此命令的效果等同于一系列`#undef`*宏名称*语句开始处的文件。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[预处理器指令](../preprocessor/preprocessor-directives.md)