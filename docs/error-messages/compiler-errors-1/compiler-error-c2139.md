---
title: 编译器错误 C2139
ms.date: 11/04/2016
f1_keywords:
- C2139
helpviewer_keywords:
- C2139
ms.assetid: 31e047c0-5bf9-46c2-b6de-b627ea6a5768
ms.openlocfilehash: f462b7d26e21b9313949bb3968b5b39e81bb30b4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50437113"
---
# <a name="compiler-error-c2139"></a>编译器错误 C2139

type： 未定义的类不允许作为编译器内部类型特征特征的参数

类型特征传递的参数无效。

有关详细信息，请参阅[编译器支持类型特征](../../windows/compiler-support-for-type-traits-cpp-component-extensions.md)。

## <a name="example"></a>示例

下面的示例生成错误 C2139。

```
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