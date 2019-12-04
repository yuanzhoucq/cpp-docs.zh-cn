---
title: 编译器错误 C3487
ms.date: 11/04/2016
f1_keywords:
- C3487
helpviewer_keywords:
- C3487
ms.assetid: 39bda474-4418-4a79-98bf-2b22fa92eaaa
ms.openlocfilehash: 7b38755470e3746066711382b2ed471badc8e197
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74738435"
---
# <a name="compiler-error-c3487"></a>编译器错误 C3487

“返回类型”: 所有返回表达式必须推导为相同类型: 以前为“返回类型”

Lambda 必须指定其返回类型，除非它包含单个返回语句。 如果 lambda 包含多个返回语句，则它们必须具有相同类型。

### <a name="to-correct-this-error"></a>更正此错误

- 为 lambda 指定结尾返回类型。 验证 lambda 的所有返回值都属于相同类型或可以隐式转换为返回类型。

## <a name="example"></a>示例

下面的示例生成 C3487，因为 lambda 的返回类型不匹配：

```cpp
// C3487.cpp
// Compile by using: cl /c /W4 C3487.cpp

int* test(int* pi) {
   // To fix the error, uncomment the trailing return type below
   auto odd_pointer = [=]() /* -> int* */ {
      if (*pi % 2)
         return pi;
      return nullptr; // C3487 - nullptr is not an int* type
   };
   return odd_pointer();
}
```

## <a name="see-also"></a>另请参阅

[Lambda 表达式](../../cpp/lambda-expressions-in-cpp.md)
