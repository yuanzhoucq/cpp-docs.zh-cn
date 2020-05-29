---
title: 编译器警告（等级 1）C4822
ms.date: 11/04/2016
f1_keywords:
- C4822
helpviewer_keywords:
- C4822
ms.assetid: 0f231a30-2eb0-4722-aaa0-e2d19d3e7eea
ms.openlocfilehash: 59c42227c7e8be9bd31c37776d9724d23db61837
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80174864"
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
