---
title: 编译器错误 C2705
ms.date: 11/04/2016
f1_keywords:
- C2705
helpviewer_keywords:
- C2705
ms.assetid: 29249ea3-4ea7-4105-944b-bdb83e8d6852
ms.openlocfilehash: 872471158d3f8c301a271dd68b2ef36839e2b9c5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62161156"
---
# <a name="compiler-error-c2705"></a>编译器错误 C2705

label： 非法跳转到异常处理程序块作用域

执行跳转到内的标签`try` / `catch`， `__try` / `__except`， `__try` / `__finally`块。 有关详细信息，请参阅[异常处理](../../cpp/exception-handling-in-visual-cpp.md)。

下面的示例生成 C2705:

```
// C2705.cpp
int main() {
goto trouble;
   __try {
      trouble: ;   // C2705
   }
   __finally {}

   // try the following line instead
   // trouble: ;
}
```