---
title: 编译器警告（等级 1）C4739
ms.date: 11/04/2016
f1_keywords:
- C4739
helpviewer_keywords:
- C4739
ms.assetid: 600873b3-7c85-4cd4-944e-cd8e01bfcbb0
ms.openlocfilehash: 9c68a9e0a2873de7e919fafbef68835f0970c03b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80185693"
---
# <a name="compiler-warning-level-1-c4739"></a>编译器警告（等级 1）C4739

对变量“var”的引用超过了其存储空间

将值赋给了变量，但是该值的大小超过变量的大小。 内存将写入变量的内存位置之外，并且可能丢失数据。

要消除此警告，仅需将值赋给其大小可容纳该值的变量。

下面的示例生成 C4739：

```cpp
// C4739.cpp
// compile with: /RTCs /Zi /W1 /c
char *pc;
int main() {
   char c;
   *(int *)&c = 1;   // C4739

   // OK
   *(char *)&c = 1;
}
```
