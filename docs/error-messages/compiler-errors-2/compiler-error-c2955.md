---
title: 编译器错误 C2955
ms.date: 03/28/2017
f1_keywords:
- C2955
helpviewer_keywords:
- C2955
ms.assetid: 77709fb6-d69b-46fd-a62f-e8564563d01b
ms.openlocfilehash: c012e5189b9ca1d0b0e786cbddacedee7c6728d2
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/10/2018
ms.locfileid: "51519992"
---
# <a name="compiler-error-c2955"></a>编译器错误 C2955

“标识符”：类模板或别名泛型的使用需要模板或泛型自变量列表

在没有模板和泛型自变量列表的情况下，你不能将类模板或类泛型用作标识符。

有关详细信息，请参阅[类模板](../../cpp/class-templates.md)。

下面的示例生成 C2955，并演示如何修复此错误：

```
// C2955.cpp
// compile with: /c
template<class T>
class X {};

X x1;   // C2955
X<int> x2;   // OK - this is how to fix it.
```

当尝试为类模板中声明的函数进行超行定义时，也可能发生 C2955：

```
// C2955_b.cpp
// compile with: /c
template <class T>
class CT {
public:
   void CTFunc();
   void CTFunc2();
};

void CT::CTFunc() {}   // C2955

// OK - this is how to fix it
template <class T>
void CT<T>::CTFunc2() {}
```

使用泛型时也可能发生 C2955：

```
// C2955_c.cpp
// compile with: /clr
generic <class T>
ref struct GC {
   T t;
};

int main() {
   GC^ g;   // C2955
   GC <int>^ g;
}
```

## <a name="example"></a>示例

**Visual Studio 2017 和更高版本：** 编译器正确地诊断缺少的模板参数列表，当模板出现在模板参数列表中 （例如作为默认模板自变量或非类型模板参数的一部分）。 下列代码在 Visual Studio 2015 中进行编译，但在 Visual Studio 2017 中引发错误。

```
template <class T> class ListNode;
template <class T> using ListNodeMember = ListNode<T> T::*;
template <class T, ListNodeMember M> class ListHead; // C2955: 'ListNodeMember': use of alias
                                                     // template requires template argument list

// correct:  template <class T, ListNodeMember<T> M> class ListHead;
```
