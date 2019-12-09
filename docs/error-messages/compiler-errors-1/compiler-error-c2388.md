---
title: 编译器错误 C2388
ms.date: 11/04/2016
f1_keywords:
- C2388
helpviewer_keywords:
- C2388
ms.assetid: 764ad2d7-cb04-425f-ba30-70989488c4a4
ms.openlocfilehash: 21658a659468a6e2a0d911af70eefdaed320446c
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74745052"
---
# <a name="compiler-error-c2388"></a>编译器错误 C2388

"symbol"：不能同时使用 __declspec （appdomain）和 \__declspec （进程）声明符号

`appdomain` 和 `process` `__declspec` 修饰符不能用于相同的符号。 变量的存储空间按进程或按应用程序域存在。

有关详细信息，请参见 [应用程序域](../../cpp/appdomain.md) 和 [过程](../../cpp/process.md)。

以下示例生成 C2388：

```cpp
// C2388.cpp
// compile with: /clr /c
__declspec(process) __declspec(appdomain) int i;   // C2388
__declspec(appdomain) int i;   // OK
```
