---
title: 编译器错误 C2006
ms.date: 11/04/2016
f1_keywords:
- C2006
helpviewer_keywords:
- C2006
ms.assetid: caaed6f7-ceb9-4742-8820-d66657c0b04d
ms.openlocfilehash: c23f17483925f25468214165fb459db577e576fc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62208994"
---
# <a name="compiler-error-c2006"></a>编译器错误 C2006

directive 应为文件名，找到 token

如指令[#include](../../preprocessor/hash-include-directive-c-cpp.md)或[#import](../../preprocessor/hash-import-directive-cpp.md)需要文件名。 若要解决此错误，请确保*令牌*是有效的文件名。 此外，将该文件名放在双引号或尖括号。

下面的示例生成 C2006:

```
// C2006.cpp
#include stdio.h   // C2006
```

可能的解决方法：

```
// C2006b.cpp
// compile with: /c
#include <stdio.h>
```