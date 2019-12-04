---
title: 编译器错误 C2297
ms.date: 11/04/2016
f1_keywords:
- C2297
helpviewer_keywords:
- C2297
ms.assetid: 65849fe5-17e1-4b7e-b50c-f508b05ddaa4
ms.openlocfilehash: 5f07d522f7594d78df566b6a4be47ad0dadd4b3d
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759082"
---
# <a name="compiler-error-c2297"></a>编译器错误 C2297

"operator"：右操作数错误

与 `operator` 一起使用的右操作数无效。

例如，编译器可能会看到你打算在其中进行函数调用的声明。

下面的示例生成 C2297：

```cpp
// C2297.cpp
struct MyStruct {
   struct Help {
      Help(float f) : m_f(f) {}
      float m_f;
   };

   MyStruct(const Help &h) : m_f(h.m_f) {}

   MyStruct(float f) : m_f(f) {}

   MyStruct operator*(const MyStruct &f1) const {
      return MyStruct(m_f * f1.m_f);
   }

private:
   float m_f;
};

int main() {
   float f1 = 1.0f;

   MyStruct m_MyStruct1 ( MyStruct::Help( f1 ) );
   // try the following line instead
   // MyStruct m_MyStruct1 = MyStruct::Help( f1 );

   MyStruct m_MyStruct2 ( MyStruct::Help( f1 ) );
   // try the following line instead
   // MyStruct m_MyStruct2 = MyStruct::Help( f1 );

   MyStruct m_MyStruct3 = m_MyStruct1 * m_MyStruct2;   // C2297
}
```
