---
title: 编译器错误 C2159
ms.date: 11/04/2016
f1_keywords:
- C2159
helpviewer_keywords:
- C2159
ms.assetid: 925a2cbd-43c9-45ee-a373-84004350b380
ms.openlocfilehash: fd845fffe9778e51af7db77144607233ed9ddefd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62174843"
---
# <a name="compiler-error-c2159"></a>编译器错误 C2159

指定了一个以上的存储类

声明包含多个存储类。

下面的示例生成 C2159：

```
// C2159.cpp
// compile with: /c
static int i;   // OK
extern static int i;   // C2159
```