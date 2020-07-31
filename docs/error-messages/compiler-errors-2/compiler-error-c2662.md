---
title: 编译器错误 C2662
ms.date: 11/04/2016
f1_keywords:
- C2662
helpviewer_keywords:
- C2662
ms.assetid: e172c2a4-f29e-4034-8232-e7dc6f83689f
ms.openlocfilehash: 5e2dd6b01db5f7d3026f14c5032ab4623eb6fb58
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220283"
---
# <a name="compiler-error-c2662"></a>编译器错误 C2662

"function"：不能将 "this" 指针从 "type1" 转换为 "type2"

编译器无法将 **`this`** 指针从转换 `type1` 为 `type2` 。

此错误可能是由于调用对象上的非 **`const`** 成员函数导致的 **`const`** 。  可能的解决方法：

- **`const`** 从对象声明中移除。

- 添加 **`const`** 到成员函数。

下面的示例生成 C2662：

```cpp
// C2662.cpp
class C {
public:
   void func1();
   void func2() const{}
} const c;

int main() {
   c.func1();   // C2662
   c.func2();   // OK
}
```

使用 **/clr**进行编译时，不能对 **`const`** 或 **`volatile`** 限定的托管类型调用函数。 不能声明托管类的 const 成员函数，因此不能对 const 托管对象调用方法。

```cpp
// C2662_b.cpp
// compile with: /c /clr
ref struct M {
   property M^ Type {
      M^ get() { return this; }
   }

   void operator=(const M %m) {
      M ^ prop = m.Type;   // C2662
   }
};

ref struct N {
   property N^ Type {
      N^ get() { return this; }
   }

   void operator=(N % n) {
      N ^ prop = n.Type;   // OK
   }
};
```

下面的示例生成 C2662：

```cpp
// C2662_c.cpp
// compile with: /c
// C2662 expected
typedef int ISXVD;
typedef unsigned char BYTE;

class LXBASE {
protected:
    BYTE *m_rgb;
};

class LXISXVD:LXBASE {
public:
   // Delete the following line to resolve.
   ISXVD *PMin() { return (ISXVD *)m_rgb; }

   ISXVD *PMin2() const { return (ISXVD *)m_rgb; };   // OK
};

void F(const LXISXVD *plxisxvd, int iDim) {
   ISXVD isxvd;
   // Delete the following line to resolve.
   isxvd = plxisxvd->PMin()[iDim];

   isxvd = plxisxvd->PMin2()[iDim];
}
```
