---
title: 编译器错误 C3417
ms.date: 11/04/2016
f1_keywords:
- C3417
helpviewer_keywords:
- C3417
ms.assetid: 3e7869ea-8948-42fb-ba30-6ccafe499c35
ms.openlocfilehash: 574af940f17c1a79472d6d20d63c9ff74d4c411e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50615757"
---
# <a name="compiler-error-c3417"></a>编译器错误 C3417

member： 值类型不能包含用户定义的特殊成员函数

值类型不能包含例如默认实例构造函数、 析构函数或复制构造函数的函数。

下面的示例生成 C3517:

```
// C3417.cpp
// compile with: /clr /c
value class VC {
   VC(){}   // C3417

   // OK
   static VC(){}
   VC(int i){}
};
```