---
title: 编译器错误 C2893
ms.date: 11/04/2016
f1_keywords:
- C2893
helpviewer_keywords:
- C2893
ms.assetid: ec0cbe43-005d-45da-8742-aaeb9b81d28e
ms.openlocfilehash: ca603eb94d5d528a7fed15e0320e1f5d88bf0629
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760871"
---
# <a name="compiler-error-c2893"></a>编译器错误 C2893

未能使函数模板 "template name" 专用化

编译器未能使函数模板专用化。 导致此错误的原因可能有很多。

通常，解决 C2893 错误的方法是查看函数的签名，并确保可以实例化每个类型。

## <a name="example"></a>示例

发生 C2893 的原因是，`f`的模板参数 `T` 被推导为要 `std::map<int,int>`，但 `std::map<int,int>` 没有成员 `data_type` （不能用`T::data_type` 来实例化 `T = std::map<int,int>`。）。 下面的示例生成 C2893。

```cpp
// C2893.cpp
// compile with: /c /EHsc
#include<map>
using namespace std;
class MyClass {};

template<class T>
inline typename T::data_type
// try the following line instead
// inline typename  T::mapped_type
f(T const& p1, MyClass const& p2);

template<class T>
void bar(T const& p1) {
    MyClass r;
    f(p1,r);   // C2893
}

int main() {
   map<int,int> m;
   bar(m);
}
```
