---
title: 编译器警告 （等级等级 1)c4744 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4744
dev_langs:
- C++
helpviewer_keywords:
- C4744
ms.assetid: f2a7d0b5-afd5-4926-abc3-cfbd367e3ff5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1754977486327e06fb56a786be523c1b2fb7b917
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46068970"
---
# <a name="compiler-warning-level-1-c4744"></a>编译器警告（等级 1）C4744

var 具有 file1 和 file2 中的不同类型: type1 和 type2

在两个文件中定义或引用的外部变量在这些文件中具有不同类型。  若要解决，请将类型定义相同，或者更改变量名称中的文件之一。

仅当文件使用 /gl 进行编译时，发出 C4744  有关详细信息，请参阅 [/GL（全程序优化）](../../build/reference/gl-whole-program-optimization.md)。

> [!NOTE]
>  C4744 通常是在 C （不 c + +） 文件中，因为 c + + 中的变量名称修饰的类型信息。  后 （下面） 的示例为 c + + 编译，你将获得链接器错误 LNK2019。

## <a name="example"></a>示例

此示例包含的第一个定义。

```
// C4744.c
// compile with: /c /GL
int global;
```

## <a name="example"></a>示例

下面的示例生成 C4744。

```
// C4744b.c
// compile with: C4744.c /GL /W1
// C4744 expected
#include <stdio.h>

extern unsigned global;

main()
{
    printf_s("%d\n", global);
}
```