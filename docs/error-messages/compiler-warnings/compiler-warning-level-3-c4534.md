---
title: 编译器警告（等级 3）C4534
ms.date: 11/04/2016
f1_keywords:
- c4534
helpviewer_keywords:
- C4534
ms.assetid: ec2adf3b-d7a1-4005-bb0c-5d219df78dc8
ms.openlocfilehash: 7d8ff442e84aa7563b1787e5a030297c034e1871
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2019
ms.locfileid: "74992054"
---
# <a name="compiler-warning-level-3-c4534"></a>编译器警告（等级 3）C4534

由于默认参数，"构造函数" 将不是类 "class" 的默认构造函数

非托管类可以有一个具有默认值的参数的构造函数，并且编译器将使用此构造函数作为默认构造函数。 用 `value` 关键字标记的类不会将具有默认值的构造函数用作默认构造函数。

有关更多信息，请参阅[类和结构](../../extensions/classes-and-structs-cpp-component-extensions.md)。

下面的示例生成 C4534：

```cpp
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
