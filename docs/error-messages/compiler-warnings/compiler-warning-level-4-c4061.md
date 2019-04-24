---
title: 编译器警告 （等级 C4061
ms.date: 04/05/2019
f1_keywords:
- C4061
helpviewer_keywords:
- C4061
ms.assetid: a99cf88e-7941-4519-8b1b-f6889d914b2f
ms.openlocfilehash: 073e3e9cb1cb5bb6b0f66157c986072227960212
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59237115"
---
# <a name="compiler-warning-level-4-c4061"></a>编译器警告 （等级 C4061

> 枚举器*标识符*的 switch 中的*枚举*没有被 case 标签显式处理

指定的枚举数*标识符*没有任何关联的处理程序`switch`语句具有`default`用例。 丢失的情况可能是疏忽，或可能不会出现问题。 它可能依赖枚举器是否由默认情况。 在未使用枚举器上的相关警告`switch`语句，其中不含`default`情况下，请参阅[C4062](compiler-warning-level-4-c4062.md)。

默认情况下，此警告处于关闭状态。 有关如何启用默认情况下处于关闭状态的警告的详细信息，请参阅[编译器警告的 Are Off by Default](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。

## <a name="example"></a>示例

下面的示例生成 C4061;添加缺少的枚举器，若要解决的案例：

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

## <a name="see-also"></a>请参阅

[编译器警告（等级 4）C4062](compiler-warning-level-4-c4062.md)
