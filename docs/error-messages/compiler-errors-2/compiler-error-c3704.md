---
title: 编译器错误 C3704
ms.date: 11/04/2016
f1_keywords:
- C3704
helpviewer_keywords:
- C3704
ms.assetid: ee40ea35-a214-4dec-9489-d7f155dd0ac2
ms.openlocfilehash: 11e5792344b6f8fba6183f4ab87e1799db803b46
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757938"
---
# <a name="compiler-error-c3704"></a>编译器错误 C3704

"function"： vararg 方法无法激发事件

您尝试对 vararg 方法使用[__event](../../cpp/event.md) 。 若要修复此错误，请将 `fireEvent(int i, ...)` 调用替换为 `fireEvent(int i)` 调用，如下面的代码示例中所示。

下面的示例生成 C3704：

```cpp
// C3704.cpp
[ event_source(native) ]
class CEventSrc {
   public:
      __event void fireEvent(int i, ...);   // C3704
      // try the following line instead:
      // __event void fireEvent(int i);
};

int main() {
}
```
