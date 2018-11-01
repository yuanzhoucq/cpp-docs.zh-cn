---
title: 编译器错误 C2733
ms.date: 11/04/2016
f1_keywords:
- C2733
helpviewer_keywords:
- C2733
ms.assetid: 67f83561-c633-407c-a2ee-f9fd16e165bf
ms.openlocfilehash: 26819f1928223b5fa96d275290105f32787057f5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50518841"
---
# <a name="compiler-error-c2733"></a>编译器错误 C2733

重载函数 function 不允许使用的第二个 C 链接

使用 C 链接声明多个重载的函数。 使用 C 链接时，只有一个窗体的指定可以是函数的外部的。 重载的函数具有相同的未修饰的名称，因为它们不能用于 C 程序。

下面的示例生成 C2733:

```
// C2733.cpp
extern "C" {
   void F1(int);
}

extern "C" {
   void F1();   // C2733
   // try the following line instead
   // void F2();
}
```