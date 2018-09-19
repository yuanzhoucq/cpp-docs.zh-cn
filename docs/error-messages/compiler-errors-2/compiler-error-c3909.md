---
title: 编译器错误 C3909 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3909
dev_langs:
- C++
helpviewer_keywords:
- C3909
ms.assetid: 0a443132-e53f-42dc-a58b-f086da3e7bfd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7bb3526f537a2eceb006f6af9e9b0faba44bf9cf
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46058700"
---
# <a name="compiler-error-c3909"></a>编译器错误 C3909

aWinRT 或托管的事件的声明必须出现在 WinRT 或托管的类型

Windows 运行时事件或托管事件是在本机类型中声明的。 要修复此错误，请在 Windows 运行时类型或托管类型中声明事件。

有关详细信息，请参阅[事件](../../windows/event-cpp-component-extensions.md)。

下面的示例生成 C3909，并演示如何修复此错误：

```
// C3909.cpp
// compile with: /clr /c
delegate void H();
class X {
   event H^ E;   // C3909 - use ref class X instead
};

ref class Y {
   static event H^ E {
      void add(H^) {}
      void remove( H^ h ) {}
      void raise( ) {}
   }
};
```