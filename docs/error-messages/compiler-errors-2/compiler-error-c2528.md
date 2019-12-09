---
title: 编译器错误 C2528
ms.date: 11/04/2016
f1_keywords:
- C2528
helpviewer_keywords:
- C2528
ms.assetid: 2ea9d583-67a8-4b16-b35f-a50eeffc03c4
ms.openlocfilehash: f8712cfbd34e852cf852cf9758446849d75d8bdc
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756261"
---
# <a name="compiler-error-c2528"></a>编译器错误 C2528

"name"：指向引用的指针非法

不能声明指向引用的指针。 在声明指针之前，取消对该变量的引用。

下面的示例生成 C2528：

```cpp
// C2528.cpp
int i;
int &ir = i;
int & (*irptr) = ir;    // C2528
```
