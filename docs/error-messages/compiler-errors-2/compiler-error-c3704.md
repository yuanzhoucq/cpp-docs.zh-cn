---
title: 编译器错误 C3704
ms.date: 11/04/2016
f1_keywords:
- C3704
helpviewer_keywords:
- C3704
ms.assetid: ee40ea35-a214-4dec-9489-d7f155dd0ac2
ms.openlocfilehash: 4e26742de6c294018f81c6f49c1719fdb11d5149
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50467093"
---
# <a name="compiler-error-c3704"></a>编译器错误 C3704

function: vararg 方法无法激发事件

你尝试使用[__event](../../cpp/event.md) vararg 方法上。 若要解决此错误，替换`fireEvent(int i, ...)`与调用`fireEvent(int i)`调用如下面的代码示例中所示。

下面的示例生成 C3704:

```
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