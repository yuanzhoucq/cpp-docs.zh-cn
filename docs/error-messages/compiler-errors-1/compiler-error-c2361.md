---
title: 编译器错误 C2361
ms.date: 11/04/2016
f1_keywords:
- C2361
helpviewer_keywords:
- C2361
ms.assetid: efbdaeb9-891c-4f7d-97da-89088a8413f3
ms.openlocfilehash: b95c6459c0ff093d22f3e754f2c7fd6564d2b296
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221193"
---
# <a name="compiler-error-c2361"></a>编译器错误 C2361

"default" 标签跳过 "identifier" 的初始化

`identifier`可以在语句中跳过的初始化 **`switch`** 。 不能跳过带有初始值设定项的声明，除非该声明括在块中。 （除非它是在块中声明的，否则在语句结束之前，该变量在范围内 **`switch`** 。）

下面的示例生成 C2361：

```cpp
// C2361.cpp
void func( void ) {
   int x;
   switch (x) {
   case 0 :
      int i = 1;
      { int j = 1; }
   default :   // C2361 error
      int k = 1;
   }
}
```

可能的解决方法：

```cpp
// C2361b.cpp
// compile with: /c
void func( void ) {
   int x = 0;
   switch (x) {
   case 0 :
      { int j = 1; int i = 1;}
   default :
      int k = 1;
   }
}
```
