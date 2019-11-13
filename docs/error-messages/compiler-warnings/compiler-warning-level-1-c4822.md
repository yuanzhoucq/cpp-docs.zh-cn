---
title: 编译器警告（等级 1）C4822
ms.date: 11/04/2016
f1_keywords:
- C4822
helpviewer_keywords:
- C4822
ms.assetid: 0f231a30-2eb0-4722-aaa0-e2d19d3e7eea
ms.openlocfilehash: f54f29fcbc6fb71033bc6d1d87c7ddb31622ee40
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051258"
---
# <a name="compiler-warning-level-1-c4822"></a>编译器警告（等级 1）C4822

“member”：局部类成员函数没有函数体

在类中声明了某个局部类成员函数，但并未定义。 若要使用局部类成员函数，必须在类中定义。 不能在类中声明而在类外定义。

在类外定义局部类成员函数将出现错误。

以下示例生成 C4822：

```cpp
// C4822.cpp
// compile with: /W1
int main() {
   struct C {
      void func1(int);   // C4822
      // try the following line instead
      // void func1(int){}
  };
}
```