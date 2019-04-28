---
title: 编译器错误 C3366
ms.date: 11/04/2016
f1_keywords:
- C3366
helpviewer_keywords:
- C3366
ms.assetid: efc55bcf-c16d-43c1-a36f-87a6165fa2a8
ms.openlocfilehash: 4d1cd510cda9957ced1d9dd5fd8fea267f39220d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62300552"
---
# <a name="compiler-error-c3366"></a>编译器错误 C3366

variable： 托管的静态数据成员或 WinRTtypes 必须在类定义中定义

尝试在 WinRT 或 .NET 类/接口定义外部引用该类或接口的静态成员。

编译器需要知道类的完整定义（以在一次传递后发出元数据）并要求在类中初始化静态数据成员。

例如，下面的示例生成 C3366，并演示如何修复此错误：

```
// C3366.cpp
// compile with: /clr /c
ref class X {
   public:
   static int i;   // initialize i here to avoid C3366
};

int X::i = 5;      // C3366
```
