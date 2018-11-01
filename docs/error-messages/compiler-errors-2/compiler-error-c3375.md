---
title: 编译器错误 C3375
ms.date: 11/04/2016
f1_keywords:
- C3375
helpviewer_keywords:
- C3375
ms.assetid: f1df78c6-e6ca-48f3-8b29-4e1710002bf3
ms.openlocfilehash: b3dfc17f9df495fe6907b816bace0dac1eff08cc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50545270"
---
# <a name="compiler-error-c3375"></a>编译器错误 C3375

“function”：不明确的委托函数

委托实例化可能已为静态成员函数，或为实例函数未绑定的委托，因此编译器出现此错误。

有关详细信息，请参阅[委托 （c + + 组件扩展）](../../windows/delegate-cpp-component-extensions.md)。

## <a name="example"></a>示例

以下示例生成 C3375：

```
// C3375.cpp
// compile with: /clr
ref struct R {
   static void f(R^) {}
   void f() {}
};

delegate void Del(R^);

int main() {
   Del ^ a = gcnew Del(&R::f);   // C3375
}
```