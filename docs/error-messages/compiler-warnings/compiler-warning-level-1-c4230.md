---
title: 编译器警告（等级1） C4230
ms.date: 11/04/2016
f1_keywords:
- C4230
helpviewer_keywords:
- C4230
ms.assetid: a4be8729-74b6-44df-a5ea-e3f45aad0f8f
ms.openlocfilehash: 668060f372a86295ef9a2cbcc1d5a6cd4ae9b2c5
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/05/2019
ms.locfileid: "73624921"
---
# <a name="compiler-warning-level-1-c4230"></a>编译器警告（等级1） C4230

使用了记时错误：修饰符/限定符交错;已忽略限定符

在 Microsoft 修饰符（如 `__cdecl`）之前使用限定符是一种过时的做法。

## <a name="example"></a>示例

```cpp
// C4230.cpp
// compile with: /W1 /LD
int __cdecl const function1();   // C4230 const ignored
```