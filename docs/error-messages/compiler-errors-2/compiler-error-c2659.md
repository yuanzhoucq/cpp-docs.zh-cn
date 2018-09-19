---
title: 编译器错误 C2659 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2659
dev_langs:
- C++
helpviewer_keywords:
- C2659
ms.assetid: b0883600-4d27-4ca7-a931-8ca6bd48654d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a658bc000ab0f7194e4806133b949ee0f7cf9ff9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46062938"
---
# <a name="compiler-error-c2659"></a>编译器错误 C2659

“operator”: 作为左操作数

函数在指定运算符的左边。 出现此错误的最常见原因是编译器已将运算符左侧的标识符分析为函数，但开发人员希望它是变量。 有关详细信息，请参阅 Wikipedia 文章[最棘手的分析](http://en.wikipedia.org/wiki/Most_vexing_parse)。 本示例显示了函数声明和容易混淆的变量定义：

```
// C2659a.cpp
// Compile using: cl /W4 /EHsc C2659a.cpp
#include <string>
using namespace std;

int main()
{
   string string1(); // string1 is a function returning string
   string string2{}; // string2 is a string initialized to empty

   string1 = "String 1"; // C2659
   string2 = "String 2";
}
```

若要解决此问题，请更改标识符的声明，使它不会被分析为函数声明。

当函数具有无法在指定的运算符左侧的表达式中使用的类型时，也可能发生错误 C2659。 本示例在代码将函数指针分配给函数时生成 C2659：

```
// C2659b.cpp
// Compile using: cl /W4 /EHsc C2659b.cpp
int func0(void) { return 42; }
int (*func1)(void);

int main()
{
   func1 = func0;
   func0 = func1; // C2659
}
```