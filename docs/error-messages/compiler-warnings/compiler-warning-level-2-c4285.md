---
title: 编译器警告（等级 2）C4285
ms.date: 11/04/2016
f1_keywords:
- C4285
helpviewer_keywords:
- C4285
ms.assetid: fa14de1f-fc19-4eec-8bea-81003636e12f
ms.openlocfilehash: c75d2d776537307fd34fa3a55807d303630dbeb5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80161967"
---
# <a name="compiler-warning-level-2-c4285"></a>编译器警告（等级 2）C4285

如果使用中缀表示法应用，则 "identifier：： operator->" 的返回类型为递归

指定的**operator > （）** 函数不能返回为其定义的类型或对其定义的类型的引用。

下面的示例生成 C4285：

```cpp
// C4285.cpp
// compile with: /W2
class C
{
public:
    C operator->();   // C4285
   // C& operator->();  C4285, also
};

int main()
{
}
```
