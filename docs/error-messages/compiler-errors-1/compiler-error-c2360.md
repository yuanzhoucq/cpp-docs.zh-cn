---
title: 编译器错误 C2360
ms.date: 11/04/2016
f1_keywords:
- C2360
helpviewer_keywords:
- C2360
ms.assetid: 51bfd2ee-8108-4777-aa93-148b9cebfa83
ms.openlocfilehash: 226fcd8a27c9abdb789b8191a5cf4e59cc4a66cc
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759901"
---
# <a name="compiler-error-c2360"></a>编译器错误 C2360

"identifier" 的初始化被 "case" 标签跳过

可以在 `switch` 语句中跳过 `identifier` 的初始化。 不能跳过带有初始值设定项的声明，除非该声明括在块中。 （除非它是在块中声明的，否则在 `switch` 语句结束之前，该变量在范围内。）

下面的示例生成 C2360：

```cpp
// C2360.cpp
int main() {
   int x = 0;
   switch ( x ) {
   case 0 :
      int i = 1;
      { int j = 1; }
   case 1 :   // C2360
      int k = 1;
   }
}
```

可能的解决方法：

```cpp
// C2360b.cpp
int main() {
   int x = 0;
   switch ( x ) {
   case 0 :
      { int j = 1; int i = 1;}
   case 1 :
      int k = 1;
   }
}
```
