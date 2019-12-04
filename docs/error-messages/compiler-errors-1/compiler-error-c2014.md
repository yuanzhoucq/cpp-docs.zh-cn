---
title: 编译器错误 C2014
ms.date: 11/04/2016
f1_keywords:
- C2014
helpviewer_keywords:
- C2014
ms.assetid: 231d8e9c-48c0-4027-99a3-245d186275ec
ms.openlocfilehash: 6c7e941970415c933b38f35b6c09247a3c0fd411
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757392"
---
# <a name="compiler-error-c2014"></a>编译器错误 C2014

预处理器命令必须作为第一个非空白空间启动

预处理器指令的 `#` 符号必须是不是空格的行中的第一个字符。

下面的示例生成 C2014：

```cpp
// C2014.cpp
int k; #include <stdio.h>   // C2014
```

可能的解决方法：

```cpp
// C2014b.cpp
// compile with: /c
int k;
#include <stdio.h>
```
