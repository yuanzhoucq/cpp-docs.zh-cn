---
title: 编译器警告 （等级 1） C4172
ms.date: 11/04/2016
f1_keywords:
- C4172
helpviewer_keywords:
- C4172
ms.assetid: a8d2bf65-d8b1-4fe3-8340-a223d7e7fde6
ms.openlocfilehash: caa71da9182c1da1d17d87d901084d0ee9badf73
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50536612"
---
# <a name="compiler-warning-level-1-c4172"></a>编译器警告 （等级 1） C4172

返回地址的本地变量或临时

一个函数返回的本地变量或临时对象的地址。 本地变量和临时对象会被销毁时某个函数返回，因此返回的地址无效。

重新设计函数，以便它不返回本地对象的地址。

下面的示例生成 C4172:

```
// C4172.cpp
// compile with: /W1 /LD
float f = 10;

const double& bar() {
// try the following line instead
// const float& bar() {
   return f;   // C4172
}
```