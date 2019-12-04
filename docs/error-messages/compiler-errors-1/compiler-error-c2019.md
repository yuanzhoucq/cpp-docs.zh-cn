---
title: 编译器错误 C2019
ms.date: 11/04/2016
f1_keywords:
- C2019
helpviewer_keywords:
- C2019
ms.assetid: 4f37b1e1-9eca-418f-a4c3-141e8512d7b6
ms.openlocfilehash: 5343d6760a7a7f2c868d92790bf9930e431e3517
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757509"
---
# <a name="compiler-error-c2019"></a>编译器错误 C2019

应为预处理器指令，却找到“character”

字符后跟 `#` 符号，但它不是预处理器指令的第一个字母。

下面的示例生成 C2019：

```cpp
// C2019.cpp
#!define TRUE 1   // C2019
```

可能的解决方法：

```cpp
// C2019b.cpp
// compile with: /c
#define TRUE 1
```
