---
title: 编译器错误 C2041 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2041
dev_langs:
- C++
helpviewer_keywords:
- C2041
ms.assetid: c9a33bb1-f9cf-47d6-bd21-7d867a8c37d5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bee199ea3ddca7ae329fc17ed6c3c013dc460eb7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46082165"
---
# <a name="compiler-error-c2041"></a>编译器错误 C2041

非法的数字基 number 为 character

指定的字符不是有效的数字 （如八进制或十六进制） 的基础。

下面的示例生成 C2041:

```
// C2041.cpp
int i = 081;   // C2041  8 is not a base 8 digit
```

可能的解决方法：

```
// C2041b.cpp
// compile with: /c
int j = 071;
```