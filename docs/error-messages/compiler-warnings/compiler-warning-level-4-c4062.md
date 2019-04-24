---
title: 编译器警告（等级 4）C4062
ms.date: 04/05/2019
f1_keywords:
- C4062
helpviewer_keywords:
- C4062
ms.assetid: 36d1c6ae-c917-4b08-bf30-2eb49ee94169
ms.openlocfilehash: 79658afc31565b708cdbd8a88f49b887cdd10cf3
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59237180"
---
# <a name="compiler-warning-level-4-c4062"></a>编译器警告（等级 4）C4062

> 枚举器*标识符*的 switch 中的*枚举*未处理

枚举器*标识符*无关联`case`处理程序中的`switch`语句，并且没有任何`default`可以捕捉到它的标签。 缺少用例可能监督，是在代码中可能出现的错误。 在未使用枚举器上的相关警告`switch`具有语句`default`情况下，请参阅[C4061](compiler-warning-level-4-c4061.md)。

默认情况下，此警告处于关闭状态。 有关如何启用默认情况下处于关闭状态的警告的详细信息，请参阅[编译器警告的 Are Off by Default](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。

## <a name="example"></a>示例

下面的示例生成 C4062，并演示如何修复此错误：

```cpp
// C4062.cpp
// compile with: /EHsc /W4
#pragma warning(default : 4062)
enum E { a, b, c };
void func ( E e ) {
   switch(e) {
      case a:
      case b:
   // case c:  // to fix, uncomment this line
      break;   // no default label
   }   // C4062, enumerator 'c' not handled
}

int main() {
}
```

## <a name="see-also"></a>请参阅

[编译器警告（等级 4）C4061](compiler-warning-level-4-c4061.md)
