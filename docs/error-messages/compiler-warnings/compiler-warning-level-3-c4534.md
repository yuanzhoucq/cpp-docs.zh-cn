---
title: 编译器警告（等级 3）C4534
ms.date: 11/04/2016
f1_keywords:
- c4534
helpviewer_keywords:
- C4534
ms.assetid: ec2adf3b-d7a1-4005-bb0c-5d219df78dc8
ms.openlocfilehash: a2af04502082f7fb30d59af5e6434161227c6d30
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50437244"
---
# <a name="compiler-warning-level-3-c4534"></a>编译器警告（等级 3）C4534

constructor 不会类 class 由于默认自变量的默认构造函数

非托管的类可以具有默认值的参数的构造函数，并且编译器将使用此为默认构造函数。 标记的类`value`关键字将不用作构造函数使用默认值对于其参数的默认构造函数。

有关详细信息，请参阅[类和结构](../../windows/classes-and-structs-cpp-component-extensions.md)。

下面的示例生成 C4534:

```
// C4534.cpp
// compile with: /W3 /clr /WX
value class MyClass {
public:
   int ii;
   MyClass(int i = 9) {   // C4534, will not be the default constructor
      i++;
   }
};

int main() {
   MyClass ^ xx = gcnew MyClass;
   xx->ii = 0;
}
```