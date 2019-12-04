---
title: 编译器错误 C2577
ms.date: 11/04/2016
f1_keywords:
- C2577
helpviewer_keywords:
- C2577
ms.assetid: fc79ef83-8362-40a2-9257-8037c3195ce4
ms.openlocfilehash: acb42f9b792b3908a153737bcec93a449b656147
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755442"
---
# <a name="compiler-error-c2577"></a>编译器错误 C2577

"member"：析构函数/终结器不能有返回类型

析构函数或终结器不能返回 `void` 或任何其他类型的值。 从析构函数定义中删除 `return` 语句。

## <a name="example"></a>示例

下面的示例生成 C2577。

```cpp
// C2577.cpp
// compile with: /c
class A {
public:
   A() {}
   ~A(){
      return 0;   // C2577
   }
};
```
