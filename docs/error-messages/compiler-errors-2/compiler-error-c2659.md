---
title: 编译器错误 C2659
ms.date: 11/04/2016
f1_keywords:
- C2659
helpviewer_keywords:
- C2659
ms.assetid: b0883600-4d27-4ca7-a931-8ca6bd48654d
ms.openlocfilehash: 1b44ef825626f60e9ae6c6e8600953959fcd7b3a
ms.sourcegitcommit: 28eae422049ac3381c6b1206664455dbb56cbfb6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/31/2019
ms.locfileid: "66449227"
---
# <a name="compiler-error-c2659"></a>编译器错误 C2659

“operator”: 作为左操作数

函数在指定运算符的左边。 出现此错误的最常见原因是编译器已将运算符左侧的标识符分析为函数，但开发人员希望它是变量。 有关详细信息，请参阅 Wikipedia 文章[最棘手的分析](https://en.wikipedia.org/wiki/Most_vexing_parse)。 本示例显示了函数声明和容易混淆的变量定义：

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