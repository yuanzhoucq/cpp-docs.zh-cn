---
title: 编译器错误 C2014 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2014
dev_langs:
- C++
helpviewer_keywords:
- C2014
ms.assetid: 231d8e9c-48c0-4027-99a3-245d186275ec
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4a9167d71e717490b89c1861abe9a9da9e0ab6a8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46064842"
---
# <a name="compiler-error-c2014"></a>编译器错误 C2014

预处理器命令必须作为第一个非空白空间启动

`#`预处理器指令的符号必须是不是空白的行上的第一个字符。

下面的示例生成 C2014:

```
// C2014.cpp
int k; #include <stdio.h>   // C2014
```

可能的解决方法：

```
// C2014b.cpp
// compile with: /c
int k;
#include <stdio.h>
```