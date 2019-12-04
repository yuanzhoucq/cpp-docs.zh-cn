---
title: 编译器错误 C3675
ms.date: 11/04/2016
f1_keywords:
- C3675
helpviewer_keywords:
- C3675
ms.assetid: 87461613-6633-430b-b95d-c7cb1bb63776
ms.openlocfilehash: 6772572d29765370d6cdbf52ed8470ff2f3f054e
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758068"
---
# <a name="compiler-error-c3675"></a>编译器错误 C3675

"function"：已定义 "property"，因此被保留

当你声明一个简单的属性时，编译器会生成 get 和 set 访问器方法，这些名称将出现在程序的作用域中。  编译器生成的名称是通过在属性名称前面加 get_ 和 set_ 来构成的。  因此，不能声明与编译器生成的访问器同名的函数。

有关更多信息，请参见 [property](../../extensions/property-cpp-component-extensions.md) 。

## <a name="example"></a>示例

下面的示例生成 C3675。

```cpp
// C3675.cpp
// compile with: /clr /c
ref struct C {
public:
   property int Size;
   int get_Size() { return 0; }   // C3675
};
```
