---
title: 编译器错误 C2006 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2006
dev_langs:
- C++
helpviewer_keywords:
- C2006
ms.assetid: caaed6f7-ceb9-4742-8820-d66657c0b04d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e9468be17584a54047563bace2b35f5cb4888b41
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46031198"
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