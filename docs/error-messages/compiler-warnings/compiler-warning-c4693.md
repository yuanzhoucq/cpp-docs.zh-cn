---
title: 编译器警告 C4693
ms.date: 10/25/2017
f1_keywords:
- C4693
helpviewer_keywords:
- C4693
ms.assetid: 72d8db01-5e6f-4794-8731-76107e8f064a
ms.openlocfilehash: cac5918eb4a1689fd215e07272958eeca48247ad
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59779435"
---
# <a name="compiler-warning-c4693"></a>编译器警告 C4693

> “class”：密封的抽象类不能具有任何实例成员“Test”

如果类型标记[密封](../../extensions/sealed-cpp-component-extensions.md)并[抽象](../../extensions/abstract-cpp-component-extensions.md)，它只能具有静态成员。

此警告被自动提升为错误。 如果你想要修改此行为，使用[#pragma 警告](../../preprocessor/warning.md)。

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