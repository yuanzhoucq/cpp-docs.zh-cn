---
title: 编译器警告（等级2） C4285
ms.date: 11/04/2016
f1_keywords:
- C4285
helpviewer_keywords:
- C4285
ms.assetid: fa14de1f-fc19-4eec-8bea-81003636e12f
ms.openlocfilehash: 326b73dcf4665c442926e68995bace60300b6ebf
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052102"
---
# <a name="compiler-warning-level-2-c4285"></a>编译器警告（等级2） C4285

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