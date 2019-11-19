---
title: 编译器警告（等级1） C4114
ms.date: 11/04/2016
f1_keywords:
- C4114
helpviewer_keywords:
- C4114
ms.assetid: 3983e1c6-e8bb-46dc-8894-e1827db48797
ms.openlocfilehash: 5662dba4339765db27d225eff2ad382ed56396ac
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626297"
---
# <a name="compiler-warning-level-1-c4114"></a>编译器警告（等级1） C4114

多次使用同一类型限定符

类型声明或定义多次使用类型限定符（**const**、 **volatile**、**有符号**或**无符号**）。 这会导致 Microsoft 扩展（/Ze）出现警告，并在 ANSI 兼容性（/Za）下出错。

下面的示例生成 C4114：

```cpp
// C4114.cpp
// compile with: /W1 /c
volatile volatile int i;   // C4114
```

下面的示例生成 C4114：

```cpp
// C4114_b.cpp
// compile with: /W1 /c
static const int const * ii;   // C4114
static const int * const iii;   // OK
```
