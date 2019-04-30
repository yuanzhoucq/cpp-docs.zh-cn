---
title: 编译器警告（等级 1）C4807
ms.date: 11/04/2016
f1_keywords:
- C4807
helpviewer_keywords:
- C4807
ms.assetid: 089c9f87-fd81-402e-9826-66a8ef1ef1fe
ms.openlocfilehash: a68596136e61aa33176365a4eff818124463b77e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62390459"
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