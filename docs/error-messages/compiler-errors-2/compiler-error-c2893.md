---
title: 编译器错误 C2893 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2893
dev_langs:
- C++
helpviewer_keywords:
- C2893
ms.assetid: ec0cbe43-005d-45da-8742-aaeb9b81d28e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 73d4f838f030db3667b08295006c2ea1df94c87b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46026174"
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