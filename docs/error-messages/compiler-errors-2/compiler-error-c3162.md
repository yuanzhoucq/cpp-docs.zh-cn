---
title: 编译器错误 C3162
ms.date: 11/04/2016
f1_keywords:
- C3162
helpviewer_keywords:
- C3162
ms.assetid: 0d4c4a24-1456-4191-b7d8-c38cb7b17c32
ms.openlocfilehash: f522a2de77e03a7c5f8f8dc774d62744417344fb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62174284"
---
# <a name="compiler-error-c3162"></a>编译器错误 C3162

type： 具有析构函数的引用类型不能用作静态数据成员 member 的类型

公共语言运行时无法知道何时运行时类还包含静态成员函数的用户定义的析构函数。

除非显式删除该对象，将永远不会运行一个析构函数。

有关详细信息，请参阅

- [/cgthreads（公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)

- [Visual C++ 64 位迁移的常见问题](../../build/common-visual-cpp-64-bit-migration-issues.md)

## <a name="example"></a>示例

下面的示例生成 C3162。

```
// C3162.cpp
// compile with: /clr /c
ref struct A {
   ~A() { System::Console::WriteLine("in destructor"); }
   static A i;   // C3162
   static A^ a = gcnew A;   // OK
};

int main() {
   A ^ a = gcnew A;
   delete a;
}
```