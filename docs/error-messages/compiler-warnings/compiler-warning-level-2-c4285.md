---
title: 编译器警告（等级 2）C4285
ms.date: 11/04/2016
f1_keywords:
- C4285
helpviewer_keywords:
- C4285
ms.assetid: fa14de1f-fc19-4eec-8bea-81003636e12f
ms.openlocfilehash: 96e1077ce3c9e60823a11aa41719738265ee703b
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2019
ms.locfileid: "64345392"
---
# <a name="compiler-warning-level-2-c4285"></a>编译器警告（等级 2）C4285

返回类型为辍-> 是递归如果应用使用中

指定**运算符-> （)** 函数不能返回的类型是定义或对为其定义的类型的引用。

下面的示例生成 C4285:

```
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