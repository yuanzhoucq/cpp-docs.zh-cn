---
title: 编译器错误 C2975
ms.date: 11/04/2016
f1_keywords:
- C2975
helpviewer_keywords:
- C2975
ms.assetid: 526f6b9d-6c76-4c12-9252-1b1d7c1e06c7
ms.openlocfilehash: 66b7c0d61cbc8141b9ed3e5f6eb329b68eb00477
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2019
ms.locfileid: "64344693"
---
# <a name="compiler-error-c2975"></a>编译器错误 C2975

> '*自变量*： 模板参数无效*类型*，应为编译时常量表达式

模板参数与模板声明中; 不匹配常量表达式应在尖括号内显示。 变量不允许作为模板自变量。 请检查模板定义，以找到正确的类型。

## <a name="example"></a>示例

下面的示例生成 C2975，并还显示了正确的使用：

```cpp
// C2975.cpp
template<int I>
class X {};

int main() {
   int i = 4, j = 2;
   X<i + j> x1;   // C2975
   X<6> x2;   // OK
}
```

当你使用时，也会发生 C2975 &#95;&#95;行&#95;&#95;作为编译时常数[/ZI](../../build/reference/z7-zi-zi-debug-information-format.md)。 一种解决方案就是将与编译[/Zi](../../build/reference/z7-zi-zi-debug-information-format.md)而不是 **/ZI**。

```cpp
// C2975b.cpp
// compile with: /ZI
// processor: x86
template<long line>
void test(void) {}

int main() {
   test<__LINE__>();   // C2975
}
```