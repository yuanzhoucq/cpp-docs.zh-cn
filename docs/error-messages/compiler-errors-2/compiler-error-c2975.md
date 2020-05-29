---
title: 编译器错误 C2975
ms.date: 11/04/2016
f1_keywords:
- C2975
helpviewer_keywords:
- C2975
ms.assetid: 526f6b9d-6c76-4c12-9252-1b1d7c1e06c7
ms.openlocfilehash: 70fc648de8bcf4f1e85edf3a12cc0b7d3d70625f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80201560"
---
# <a name="compiler-error-c2975"></a>编译器错误 C2975

> "*argument*"： "*type*" 的模板参数无效，应为编译时常量表达式

模板参数与模板声明不匹配;常数表达式应出现在尖括号中。 不允许将变量作为模板实际参数。 请检查模板定义，以找到正确的类型。

## <a name="example"></a>示例

下面的示例生成 C2975，并显示正确的用法：

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

当&#95; &#95;你使用 LINE&#95; &#95;作为编译时常量并使用[/zi](../../build/reference/z7-zi-zi-debug-information-format.md)时，也会发生 C2975。 一种解决方案是用[/zi](../../build/reference/z7-zi-zi-debug-information-format.md) （而不是 **/zi**）进行编译。

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
