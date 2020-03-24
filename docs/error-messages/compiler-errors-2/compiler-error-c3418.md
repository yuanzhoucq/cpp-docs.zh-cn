---
title: 编译器错误 C3418
ms.date: 11/04/2016
f1_keywords:
- C3418
helpviewer_keywords:
- C3418
ms.assetid: 54042c04-3c45-41c1-bad7-90f9ee05a21b
ms.openlocfilehash: 21023bfb551a1894e25cc4940892dde0f0440a0e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80200871"
---
# <a name="compiler-error-c3418"></a>编译器错误 C3418

不支持访问说明符“specifier”

不正确地指定了 CLR 访问说明符。  有关详细信息，请参阅[如何：定义和使用类和结构C++（/cli）](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md)中的类型可见性和成员可见性。

## <a name="example"></a>示例

下面的示例生成 C3418。

```cpp
// C3418.cpp
// compile with: /clr /c
ref struct m {
internal public:   // C3418
   void test(){}
};

ref struct n {
internal:   // OK
   void test(){}
};
```
