---
title: 编译器错误 C3828 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3828
dev_langs:
- C++
helpviewer_keywords:
- C3828
ms.assetid: 8d9cee75-9504-4bc8-88b6-2413618a3f45
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f91a4a414a881aced6e537c0b98e69896aeeb4c3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46085480"
---
# <a name="compiler-error-c3828"></a>编译器错误 C3828

object type： 时创建的实例托管，不允许使用位置自变量或 WinRTclasses

创建托管的类型或 Windows 运行时类型的对象时，不能使用运算符的放置形式[ref new、 gcnew](../../windows/ref-new-gcnew-cpp-component-extensions.md)或[新](../../cpp/new-operator-cpp.md)。

下列示例生成 C3828 并演示如何修复此错误：

```
// C3828a.cpp
// compile with: /clr
ref struct M {
};

ref struct N {
   static array<char>^ bytes = gcnew array<char>(256);
};

int main() {
   M ^m1 = new (&N::bytes) M();   // C3828
   // The following line fixes the error.
   // M ^m1 = gcnew M();
}
```