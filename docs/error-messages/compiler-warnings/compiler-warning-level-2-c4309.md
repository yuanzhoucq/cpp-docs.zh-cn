---
title: 编译器警告（等级 2）C4309
ms.date: 11/04/2016
f1_keywords:
- C4309
helpviewer_keywords:
- C4309
ms.assetid: cb3f41ef-fd8a-4def-baa1-924e751fca68
ms.openlocfilehash: 41184571dc07213c796c039170966a0c7150bd45
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62402471"
---
# <a name="compiler-warning-level-2-c4309"></a>编译器警告（等级 2）C4309

conversion： 截断常量值

类型转换会导致一个常量，以超过为其分配的空间。 您可能需要使用更大的类型的常量。

下面的示例生成 C4309:

```
// C4309.cpp
// compile with: /W2
int main()
{
   char c = 128;   // C4309
}
```