---
title: 编译器错误 C2705
ms.date: 11/04/2016
f1_keywords:
- C2705
helpviewer_keywords:
- C2705
ms.assetid: 29249ea3-4ea7-4105-944b-bdb83e8d6852
ms.openlocfilehash: 1cd46db8e4cb237bebd9568409ecadf0ff84cdf8
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758302"
---
# <a name="compiler-error-c2705"></a>编译器错误 C2705

"label"：非法跳转到 "异常处理程序块" 范围

执行将跳转到 `try`/`catch`，`__try`/`__except``__try`/`__finally` 块中的标签。 有关详细信息，请参阅[异常处理](../../cpp/exception-handling-in-visual-cpp.md)。

下面的示例生成 C2705：

```cpp
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
