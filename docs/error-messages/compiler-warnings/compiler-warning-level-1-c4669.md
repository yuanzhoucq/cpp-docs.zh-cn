---
title: 编译器警告（等级1） C4669
ms.date: 11/04/2016
f1_keywords:
- C4669
helpviewer_keywords:
- C4669
ms.assetid: 97730679-e3dc-44d4-b2a8-aa65badc17f2
ms.openlocfilehash: 58f7150caeb3e06ba400a08c6e484f677a8deff9
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051391"
---
# <a name="compiler-warning-level-1-c4669"></a>编译器警告（等级1） C4669

“cast”: 不安全的转换:“class”是托管的或 WinRT 类型对象

转换包含 Windows 运行时或托管类型。 编译器通过执行到一个指针到另一个指针的按位复制完成转换，但不提供其他检查。 若要解决此警告，请不要转换包含托管成员或 Windows 运行时类型的类。

下面的示例生成 C4669，并演示如何修复此错误：

```cpp
// C4669.cpp
// compile with: /clr /W1
ref struct A {
   int i;
   Object ^ pObj;   // remove the managed member to fix the warning
};

ref struct B {
   int j;
};

int main() {
   A ^ a = gcnew A;
   B ^ b = reinterpret_cast<B ^>(a);   // C4669
}
```