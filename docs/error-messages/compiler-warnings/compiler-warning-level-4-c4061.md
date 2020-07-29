---
title: 编译器警告（等级4） C4061
ms.date: 04/05/2019
f1_keywords:
- C4061
helpviewer_keywords:
- C4061
ms.assetid: a99cf88e-7941-4519-8b1b-f6889d914b2f
ms.openlocfilehash: 18c5a51e24af36c5a330e10a66ce3dcc38295fb1
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225275"
---
# <a name="compiler-warning-level-4-c4061"></a>编译器警告（等级4） C4061

> 枚举器 "*enumeration*" 的 switch 中的枚举器 "*identifier*" 未由 case 标签显式处理

指定的枚举器*标识符*在 **`switch`** 具有 case 的语句中没有关联的处理程序 **`default`** 。 缺少这种情况可能是一个监督，或者这可能不是问题。 这可能取决于枚举器是否是由默认事例处理的。 有关没有事例的语句中未使用的枚举器的相关警告 **`switch`** **`default`** ，请参阅[C4062](compiler-warning-level-4-c4062.md)。

默认情况下，此警告处于关闭状态。 有关如何启用默认情况下处于关闭状态的警告的详细信息，请参阅[默认情况下处于关闭状态的编译器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。

## <a name="example"></a>示例

下面的示例生成 C4061;添加缺少的枚举器修复方法：

```cpp
// C4061.cpp
// compile with: /W4
#pragma warning(default : 4061)

enum E { a, b, c };
void func ( E e )
{
   switch(e)
   {
      case a:
      case b:
      default:
         break;
   }   // C4061 c' not handled
}

int main()
{
}
```

## <a name="see-also"></a>另请参阅

[编译器警告（等级4） C4062](compiler-warning-level-4-c4062.md)
