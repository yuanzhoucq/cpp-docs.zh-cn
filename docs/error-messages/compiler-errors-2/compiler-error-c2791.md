---
title: 编译器错误 C2791
ms.date: 11/04/2016
f1_keywords:
- C2791
helpviewer_keywords:
- C2791
ms.assetid: 938ad1fb-75d9-4ce2-ad92-83d6249005b5
ms.openlocfilehash: d589094f117135474d1a8788867d2d571bbb5f5d
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74739540"
---
# <a name="compiler-error-c2791"></a>编译器错误 C2791

非法使用 "super"： "class" 没有任何基类

关键字[super](../../cpp/super.md)用于不包含任何基类的类的成员函数的上下文中。

下面的示例生成 C2791：

```cpp
// C2791.cpp
struct D {
   void mf() {
      __super::mf();   // C2791
   }
};
```
