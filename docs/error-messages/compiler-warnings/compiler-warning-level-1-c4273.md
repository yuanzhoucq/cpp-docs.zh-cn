---
title: 编译器警告 （等级 1） C4273 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4273
dev_langs:
- C++
helpviewer_keywords:
- C4273
ms.assetid: cc18611d-9454-40a4-ad73-69823d5888fb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3fb8be688fa90a015996c1ba056ef368fbc1c588
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46042086"
---
# <a name="compiler-warning-level-1-c4273"></a>编译器警告（等级 1）C4273

function： 不一致的 DLL 链接

在使用不同的文件中的两个定义[dllimport](../../cpp/dllexport-dllimport.md)。

## <a name="example"></a>示例

下面的示例生成 C4273。

```
// C4273.cpp
// compile with: /W1 /c
char __declspec(dllimport) c;
char c;   // C4273, delete this line or the line above to resolve
```

## <a name="example"></a>示例

下面的示例生成 C4273。

```
// C4273_b.cpp
// compile with: /W1 /clr /c
#include <stdio.h>
extern "C" int printf_s(const char *, ...);   // C4273
```