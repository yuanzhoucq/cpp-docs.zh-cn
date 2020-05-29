---
title: 编译器警告（等级 1）C4548
ms.date: 11/04/2016
f1_keywords:
- C4548
helpviewer_keywords:
- C4548
ms.assetid: 2cee817e-e463-4d90-bbd2-de120d48c101
ms.openlocfilehash: 3770810ae4b2e8550fa79db27b58c581414316b5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80186226"
---
# <a name="compiler-warning-level-1-c4548"></a>编译器警告（等级 1）C4548

逗号前的表达式不起任何作用；应输入带副作用的表达式

编译器检测到格式错误的逗号表达式。

默认情况下，此警告处于关闭状态。 有关详细信息，请参阅 [Compiler Warnings That Are Off by Default](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。

下面的示例生成 C4548：

```cpp
// C4548.cpp
// compile with: /W1
#pragma warning (default : 4548)
int main()
{
   int i = 0, k = 0;

   if ( i, k )   // C4548
   // try the following line instead
   // if ( i = 0, k )
      i++;
}
```
