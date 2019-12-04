---
title: 编译器错误 C3366
ms.date: 11/04/2016
f1_keywords:
- C3366
helpviewer_keywords:
- C3366
ms.assetid: efc55bcf-c16d-43c1-a36f-87a6165fa2a8
ms.openlocfilehash: 5173b1c0df7de6a4e8d9993e680b961a82bb10a7
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74738461"
---
# <a name="compiler-error-c3366"></a>编译器错误 C3366

"variable"：托管或 WinRTtypes 的静态数据成员必须在类定义中定义

尝试在 WinRT 或 .NET 类/接口定义外部引用该类或接口的静态成员。

编译器需要知道类的完整定义（以在一次传递后发出元数据）并要求在类中初始化静态数据成员。

例如，下面的示例生成 C3366，并演示如何修复此错误：

```cpp
// C3366.cpp
// compile with: /clr /c
ref class X {
   public:
   static int i;   // initialize i here to avoid C3366
};

int X::i = 5;      // C3366
```
