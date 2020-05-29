---
title: 编译器警告（等级 1）C4033
ms.date: 11/04/2016
f1_keywords:
- C4033
helpviewer_keywords:
- C4033
ms.assetid: 189a9ec3-ff6d-49dd-b9b2-530b28bbb7c9
ms.openlocfilehash: d5bee2eb874b965ff99e3dc0038d63d65b346318
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80164347"
---
# <a name="compiler-warning-level-1-c4033"></a>编译器警告（等级 1）C4033

“function”必须返回值

此函数未返回值。 返回了一个未定义的值。

必须将使用 `return` 且没有返回值的函数声明为 `void`类型。

此错误针对 C 语言代码。

以下示例生成 C4033：

```c
// C4033.c
// compile with: /W1 /LD
int test_1(int x)   // C4033 expected
{
   if (x)
   {
      return;   // C4033
   }
}
```
