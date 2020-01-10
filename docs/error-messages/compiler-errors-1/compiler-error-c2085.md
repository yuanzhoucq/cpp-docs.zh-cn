---
title: 编译器错误 C2085
ms.date: 11/04/2016
f1_keywords:
- C2085
helpviewer_keywords:
- C2085
ms.assetid: 0a86785c-8e6f-481b-8c7b-412220c1950d
ms.openlocfilehash: 7dbf7266a6330a1fdb46d7f2df90e7684f026d9a
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301959"
---
# <a name="compiler-error-c2085"></a>编译器错误 C2085

"identifier"：不在形参表中

已在函数定义中声明该标识符，但在形参表中未声明。 （仅限 ANSI C）

下面的示例生成 C2085：

```c
// C2085.c
void func1( void )
int main( void ) {}   // C2085
```

可能的解决方法：

```c
// C2085b.c
void func1( void );
int main( void ) {}
```

缺少分号后，`func1()` 看起来像函数定义，而不是原型，因此 `main` 在 `func1()`中定义，从而为标识符 `main`生成错误 C2085。
