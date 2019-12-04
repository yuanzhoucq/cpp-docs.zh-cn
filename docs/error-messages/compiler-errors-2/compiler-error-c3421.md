---
title: 编译器错误 C3421
ms.date: 11/04/2016
f1_keywords:
- C3421
helpviewer_keywords:
- C3421
ms.assetid: b52050c6-17a4-424a-8894-337b0cec7010
ms.openlocfilehash: 39a57aa7b85b9f8a8aae0b93e2b346584edef8de
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756235"
---
# <a name="compiler-error-c3421"></a>编译器错误 C3421

“type”: 由于该类的终结器不可访问或不存在，因此无法调用它

终结器属于隐式专用，因此无法从其封闭类型外调用它。

有关详细信息，请参阅[如何：定义和使用类和结构（C++/cli）中的析构函数和终结](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers)器。

## <a name="example"></a>示例

下面的示例生成 C3421。

```cpp
// C3421.cpp
// compile with: /clr
ref class A {};

ref class B {
   !B() {}

public:
   ~B() {}
};

int main() {
   A a;
   a.!A();   // C3421

   B b;
   b.!B();   // C3421
}
```
