---
title: 创建内联文件文本
ms.date: 11/04/2016
helpviewer_keywords:
- inline files, creating text
- NMAKE program, inline files
- text, inline file
ms.assetid: b8a332ed-8244-4ff8-89e6-029d7f659725
ms.openlocfilehash: 4989d0757e893a7bc4b0a0e8937afee18719aa4e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50523084"
---
# <a name="creating-inline-file-text"></a>创建内联文件文本

内联文件可以是临时的还是永久。

## <a name="syntax"></a>语法

```
inlinetext
.
.
.
<<[KEEP | NOKEEP]
```

## <a name="remarks"></a>备注

指定*inlinetext*在命令后的第一行上。 在单独一行的开头用两个尖括号 (<<) 标记末尾。 该文件包含所有*inlinetext*分隔括号之前。 *Inlinetext*可以具有宏扩展和替换项，但不是指令或生成文件的注释。 原义处理空格、 制表符和换行字符。

临时文件在会话期间存在，并且可以由其他命令重复使用。 指定**保留**右尖括号后 NMAKE 会话; 保留文件后未命名的文件将保留在磁盘上使用生成的文件名。 指定**NOKEEP**或 nothing 的临时文件。 **保持**并**NOKEEP**不区分大小写。

## <a name="see-also"></a>请参阅

[生成文件中的内联文件](../build/inline-files-in-a-makefile.md)