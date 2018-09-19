---
title: 编译器警告 （等级 1） C4227 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4227
dev_langs:
- C++
helpviewer_keywords:
- C4227
ms.assetid: 78f98374-c00b-4000-aefa-1b1c67b4666b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fda3a31b228f16b27f4bdefd3131a0ddcb90f5b5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46060847"
---
# <a name="compiler-warning-level-1-c4227"></a>编译器警告（等级 1）C4227

使用了记时错误： 忽略引用上的限定符

使用等限定符`const`或`volatile`与 c + + 引用是过时的做法。

## <a name="example"></a>示例

```
// C4227.cpp
// compile with: /W1 /c
int j = 0;
int &const i = j;   // C4227
```