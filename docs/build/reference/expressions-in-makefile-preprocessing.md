---
title: 生成文件预处理中的表达式
ms.date: 11/04/2016
helpviewer_keywords:
- preprocessing makefiles
- expressions [C++], makefile preprocessing
- makefiles, preprocessing
ms.assetid: 37f0f413-97e0-452c-a83f-3c9002c44c92
ms.openlocfilehash: 3d668492441eb2fc09be378dbebfe2b18c1b5753
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57825127"
---
# <a name="expressions-in-makefile-preprocessing"></a>生成文件预处理中的表达式

**！如果**或 **！ELSE IF** `constantexpression`组成 （采用十进制或 C 语言表示法） 的整数常量、 字符串常量或命令。 使用括号将组表达式。 表达式使用 C 样式带符号长整数算术;数字是 32 位的 2 的补数形式的范围中-2147483648 到 2147483647。

表达式可以使用常量值、 命令、 字符串、 宏和文件系统路径中的退出代码在处理的运算符。

## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？

[生成文件预处理运算符](makefile-preprocessing-operators.md)

[在预处理中执行程序](executing-a-program-in-preprocessing.md)

## <a name="see-also"></a>请参阅

[生成文件预处理](makefile-preprocessing.md)
