---
title: 编译器错误 C3367
ms.date: 11/04/2016
f1_keywords:
- C3367
helpviewer_keywords:
- C3367
ms.assetid: e675d42b-f5b0-4d43-aab1-1f5024233102
ms.openlocfilehash: bedc94039f8621a93672c0dfa0cad5a54aad796e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80201157"
---
# <a name="compiler-error-c3367"></a>编译器错误 C3367

“static_member_function”: 不能使用静态函数创建未绑定的委托

当你调用未绑定的委托时，必须传递对象的实例。 由于通过类名称调用静态成员函数，因此仅能通过实例成员函数实例化未绑定的委托。

有关未绑定委托的详细信息，请参阅[如何：定义和使用委托C++（/cli）](../../dotnet/how-to-define-and-use-delegates-cpp-cli.md)。

## <a name="example"></a>示例

以下示例生成 C3367。

```cpp
// C3367.cpp
// compile with: /clr
ref struct R {
   void b() {}
   static void f() {}
};

delegate void Del(R^);

int main() {
   Del ^ a = gcnew Del(&R::b);   // OK
   Del ^ b = gcnew Del(&R::f);   // C3367
}
```
