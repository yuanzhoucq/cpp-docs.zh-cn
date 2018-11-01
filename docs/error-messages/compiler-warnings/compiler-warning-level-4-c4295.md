---
title: 编译器警告（等级 4）C4295
ms.date: 1/09/2018
f1_keywords:
- C4295
helpviewer_keywords:
- C4295
ms.assetid: 20dbff85-9f62-4ca3-8fe9-079d4512006d
ms.openlocfilehash: ed31ea19f9c36a9c6fab7452a4bfc3843a151059
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50472184"
---
# <a name="compiler-warning-level-4-c4295"></a>编译器警告（等级 4）C4295

> '*数组*： 数组是太小，无法包括终止 null 字符

已初始化数组，但数组中的最后一个字符不为 null;访问数组作为一个字符串，可能会产生意外的结果。

## <a name="example"></a>示例

下面的示例生成 C4295。 若要解决此问题，您可以声明数组大小较大，以保留终止 null 的初始值设定项字符串，或者也可以使用数组初始值设定项列表进行的意图更明显，这是一个数组`char`，不是以 null 结尾的字符串。

```C
// C4295.c
// compile with: /W4

int main() {
   char a[3] = "abc";           // C4295
   char b[3] = {'d', 'e', 'f'}; // No warning
   a[0] = b[2];
}
```
