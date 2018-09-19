---
title: 编译器错误 C3162 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3162
dev_langs:
- C++
helpviewer_keywords:
- C3162
ms.assetid: 0d4c4a24-1456-4191-b7d8-c38cb7b17c32
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 529dfa41064e9d22b796b9d079a67b213b816fb2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46030932"
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