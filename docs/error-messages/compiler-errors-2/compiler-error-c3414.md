---
title: 编译器错误 C3414
ms.date: 11/04/2016
f1_keywords:
- C3414
helpviewer_keywords:
- C3414
ms.assetid: 715f5432-b509-4f8f-84f5-e1463bac490f
ms.openlocfilehash: 86ed40f31ae17724700e9d2c68950027d0eefb69
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50608969"
---
# <a name="compiler-error-c3414"></a>编译器错误 C3414

member： 不能定义导入的成员函数

此外定义中引用的程序集中的代码中定义的成员。

下面的示例生成 C3414:

```
// C3414a2.cpp
// compile with: /clr /LD
public ref class MyClass {
public:
   void Test(){}
};
```

然后：

```
// C3414b2.cpp
// compile with: /clr
#using <C3414a2.dll>

void MyClass::Test() {    // C3414
}

System::Object::Object() {    // C3414
}
```
