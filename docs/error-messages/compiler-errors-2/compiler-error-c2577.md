---
title: 编译器错误 C2577
ms.date: 11/04/2016
f1_keywords:
- C2577
helpviewer_keywords:
- C2577
ms.assetid: fc79ef83-8362-40a2-9257-8037c3195ce4
ms.openlocfilehash: 0a7c711fa399c1bf31bc9de61f0b77ad19172a73
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87206908"
---
# <a name="compiler-error-c2577"></a>编译器错误 C2577

"member"：析构函数/终结器不能有返回类型

析构函数或终结器不能返回 **`void`** 或任何其他类型的值。 **`return`** 从析构函数定义中删除语句。

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
