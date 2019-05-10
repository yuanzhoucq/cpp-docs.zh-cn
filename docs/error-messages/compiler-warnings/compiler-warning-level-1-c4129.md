---
title: 编译器警告 （等级 1） C4129
ms.date: 11/04/2016
f1_keywords:
- C4129
helpviewer_keywords:
- C4129
ms.assetid: a4190c64-4bfb-48fd-8e98-52720bc0d878
ms.openlocfilehash: dc4f4c4c1feeba543ce0baa71e1ee5dfd81fdcae
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62310943"
---
# <a name="compiler-warning-level-1-c4129"></a>编译器警告 （等级 1） C4129

character： 无法识别的字符转义序列

`character`反斜杠 (\\) 中的字符或字符串常量未识别为有效的转义序列。 反斜杠被忽略，不打印。 打印对反斜杠后面的字符。

若要打印单个反斜杠，请指定双反斜杠 (\\\\)。

C++ Standard、 2.13.2 节中的讨论了转义序列。

下面的示例生成 C4129:

```
// C4129.cpp
// compile with: /W1
int main() {
   char array1[] = "\/709";   // C4129
   char array2[] = "\n709";   // OK
}
```