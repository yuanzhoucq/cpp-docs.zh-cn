---
title: 编译器错误 C3063
ms.date: 11/04/2016
f1_keywords:
- C3063
helpviewer_keywords:
- C3063
ms.assetid: 0ecf6f1f-e4a7-487a-9fd5-79d8ac470001
ms.openlocfilehash: c52a0a4c4255eeed5f49a7e6c1e86a1f64b8ad77
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755650"
---
# <a name="compiler-error-c3063"></a>编译器错误 C3063

运算符 "operator"：所有操作数必须具有相同的枚举类型

对枚举器使用运算符时，两个操作数必须是枚举类型。 有关详细信息，请参阅[如何：在/cli 中C++定义和使用枚举](../../dotnet/how-to-define-and-consume-enums-in-cpp-cli.md)。

## <a name="example"></a>示例

下面的示例生成 C3063，并演示如何修复此问题：

```cpp
// C3063.cpp
// compile with: /clr
enum class E { a, b } e, mask;
int main() {
   if ( ( e & mask ) != 0 ) ;   // C3063 no operator!= (E, int)

   if ( ( e & mask ) != E() )   // OK
      ;
}
```
