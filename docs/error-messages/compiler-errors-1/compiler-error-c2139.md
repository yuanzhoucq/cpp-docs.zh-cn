---
title: 编译器错误 C2139
ms.date: 11/04/2016
f1_keywords:
- C2139
helpviewer_keywords:
- C2139
ms.assetid: 31e047c0-5bf9-46c2-b6de-b627ea6a5768
ms.openlocfilehash: 38e2fd090f3a2b2222658c5fd491c84dd70fd5ea
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756417"
---
# <a name="compiler-error-c2139"></a>编译器错误 C2139

"type"：未定义的类不允许作为编译器内部类型特征 "特征" 的参数

传递给类型特征的参数无效。

有关详细信息，请参阅[编译器对类型特征的支持](../../extensions/compiler-support-for-type-traits-cpp-component-extensions.md)。

## <a name="example"></a>示例

下面的示例生成 C2139。

```cpp
// C2139.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

template <class T>
struct is_polymorphic {
   static const bool value = __is_polymorphic(T);
};

class C;
class D {};

class E {
public:
   virtual void Test() {}
};

int main() {
   cout << is_polymorphic<C>::value << endl;   // C2139
   cout << is_polymorphic<D>::value << endl;   // OK
   cout << is_polymorphic<E>::value << endl;   // OK
}
```
