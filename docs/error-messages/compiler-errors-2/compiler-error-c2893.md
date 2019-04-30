---
title: 编译器错误 C2893
ms.date: 11/04/2016
f1_keywords:
- C2893
helpviewer_keywords:
- C2893
ms.assetid: ec0cbe43-005d-45da-8742-aaeb9b81d28e
ms.openlocfilehash: f1fad1ad18af54945ef32dadaac50a6de4dbd62f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62366376"
---
# <a name="compiler-error-c2893"></a>编译器错误 C2893

未能特殊化函数模板模板名称

编译器未能特殊化函数模板。 可以有许多原因导致此错误。

一般情况下，若要解决 C2893 错误的方式是查看函数的签名并确保可以实例化每个类型。

## <a name="example"></a>示例

C2893 的发生是因为`f`的模板参数`T`推导为`std::map<int,int>`，但`std::map<int,int>`没有成员`data_type`(`T::data_type`不使用实例化`T = std::map<int,int>`。)。 下面的示例生成 C2893。

```
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