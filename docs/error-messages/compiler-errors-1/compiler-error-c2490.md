---
title: 编译器错误 C2490
ms.date: 11/04/2016
f1_keywords:
- C2490
helpviewer_keywords:
- C2490
ms.assetid: 9de6bddd-b2e2-4ce6-b33b-201a8c2c8c54
ms.openlocfilehash: 9e06883d0e8b6103eb44d086d3872d86c50a58b6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62361799"
---
# <a name="compiler-error-c2490"></a>编译器错误 C2490

keyword 具有 naked 特性的函数中不允许

定义为一个函数[裸](../../cpp/naked-cpp.md)不能使用结构化的异常处理。

下面的示例生成 C2490:

```
// C2490.cpp
// processor: x86
__declspec( naked ) int func() {
   __try{}   // C2490, structured exception handling
}
```