---
title: 编译器错误 C2012
ms.date: 11/04/2016
f1_keywords:
- C2012
helpviewer_keywords:
- C2012
ms.assetid: 9f0d8162-c0b3-4234-a41f-836fdb75c84e
ms.openlocfilehash: a04f4a1758c9adb6e72b11881d18d210c9f36206
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74752387"
---
# <a name="compiler-error-c2012"></a>编译器错误 C2012

"<" 后缺少名称

`#include` 指令缺少必需的文件名。

以下示例生成 C2012：

```cpp
// C2012.cpp
#include <   // C2012 include the filename to resolve
```

可能的解决方法：

```cpp
// C2012b.cpp
// compile with: /c
#include <stdio.h>
```
