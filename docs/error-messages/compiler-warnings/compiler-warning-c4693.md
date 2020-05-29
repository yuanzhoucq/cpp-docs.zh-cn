---
title: 编译器警告 C4693
ms.date: 10/25/2017
f1_keywords:
- C4693
helpviewer_keywords:
- C4693
ms.assetid: 72d8db01-5e6f-4794-8731-76107e8f064a
ms.openlocfilehash: 71c3db18b400ce94bff3c643d6728a6613061039
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165127"
---
# <a name="compiler-warning-c4693"></a>编译器警告 C4693

> “class”：密封的抽象类不能具有任何实例成员“Test”

如果类型标记为[sealed](../../extensions/sealed-cpp-component-extensions.md)和[abstract](../../extensions/abstract-cpp-component-extensions.md)，则它只能具有静态成员。

此警告会自动提升为错误。 如果要修改此行为，请使用[#pragma 警告](../../preprocessor/warning.md)。

## <a name="example"></a>示例

下面的示例生成 C4693。

```cpp
// C4693.cpp
// compile with: /clr /c
public ref class Public_Ref_Class sealed abstract {
public:
   void Test() {}   // C4693
   static void Test2() {}   // OK
};
```
