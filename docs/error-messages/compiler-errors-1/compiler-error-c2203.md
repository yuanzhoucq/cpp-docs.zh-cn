---
title: 编译器错误 C2203
ms.date: 11/04/2016
f1_keywords:
- C2203
helpviewer_keywords:
- C2203
ms.assetid: 5497df43-86f6-43d5-b6cb-723c4c589b10
ms.openlocfilehash: 4a078cd4c64bbb8d301aa3e4817272d23e3acbb4
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216305"
---
# <a name="compiler-error-c2203"></a>编译器错误 C2203

删除运算符不能指定数组的边界

使用 **/za** （ANSI）选项， **`delete`** 运算符可以删除整个数组，但不能删除数组的部分或特定成员。

下面的示例生成 C2203：

```cpp
// C2203.cpp
// compile with: /Za
int main() {
   int *ar = new int[10];
   delete [4] ar;   // C2203
   // try the following line instead
   // delete [] ar;
}
```
