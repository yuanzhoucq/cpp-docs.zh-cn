---
title: 编译器错误 C2019 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2019
dev_langs:
- C++
helpviewer_keywords:
- C2019
ms.assetid: 4f37b1e1-9eca-418f-a4c3-141e8512d7b6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e6f1ae1b22cca0d00e990f64ccaf469359563f8e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46038693"
---
# <a name="compiler-error-c2019"></a>编译器错误 C2019

应为预处理器指令，却找到“character”

字符跟在`#`登录，但这不是预处理器指令的第一个字母。

下面的示例生成 C2019:

```
// C2019.cpp
#!define TRUE 1   // C2019
```

可能的解决方法：

```
// C2019b.cpp
// compile with: /c
#define TRUE 1
```