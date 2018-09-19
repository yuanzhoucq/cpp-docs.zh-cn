---
title: 编译器警告 （等级 1） C4807 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4807
dev_langs:
- C++
helpviewer_keywords:
- C4807
ms.assetid: 089c9f87-fd81-402e-9826-66a8ef1ef1fe
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e8eecbd1e7c9c88ec463224b9738cebbf9ff8f4d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46039863"
---
# <a name="compiler-warning-level-1-c4807"></a>编译器警告（等级 1）C4807

“operation”: 类型“type”与类型“type”的有符号位域的混合不安全

在将一位有符号位域与 `bool` 变量进行比较时生成此警告。 因为一位有符号位域只能包含值 -1 或 0，所以将其与 `bool`比较很危险。 将 `bool` 与一位无符号位域进行混合不生成警告，因为它们与 `bool` 相同，只包含 0 或 1。

## <a name="example"></a>示例

下面的示例生成 C4807：

```
// C4807.cpp
// compile with: /W1
typedef struct bitfield {
   signed mybit : 1;
} mybitfield;

int main() {
   mybitfield bf;
   bool b = true;

   // try..
   // int b = true;

   bf.mybit = -1;
   if (b == bf.mybit) {   // C4807
      b = false;
   }
}
```