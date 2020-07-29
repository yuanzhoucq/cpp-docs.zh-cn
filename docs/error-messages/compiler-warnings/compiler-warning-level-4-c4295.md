---
title: 编译器警告（等级 4）C4295
ms.date: 01/09/2018
f1_keywords:
- C4295
helpviewer_keywords:
- C4295
ms.assetid: 20dbff85-9f62-4ca3-8fe9-079d4512006d
ms.openlocfilehash: d960e5a5e2d7ad2d2b650095c42e9afea7bfe7fb
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219867"
---
# <a name="compiler-warning-level-4-c4295"></a>编译器警告（等级 4）C4295

> "*array*"：数组太小，无法包括终止 null 字符

数组已初始化，但数组中的最后一个字符不是 null;以字符串的形式访问数组可能会产生意外的结果。

## <a name="example"></a>示例

下面的示例生成 C4295。 若要解决此问题，你可以将数组大小声明得更大，以便在初始值设定项字符串中保存终止 null，或者可以使用数组初始值设定项列表来清楚地表明，这是的数组 **`char`** ，而不是以 null 结尾的字符串。

```C
// C4295.c
// compile with: /W4

int main() {
   char a[3] = "abc";           // C4295
   char b[3] = {'d', 'e', 'f'}; // No warning
   a[0] = b[2];
}
```
