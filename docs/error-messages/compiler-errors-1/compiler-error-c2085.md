---
title: 编译器错误 C2085
ms.date: 11/04/2016
f1_keywords:
- C2085
helpviewer_keywords:
- C2085
ms.assetid: 0a86785c-8e6f-481b-8c7b-412220c1950d
ms.openlocfilehash: a65e3c0ea622950b99b9ba83fc168b4718d13e46
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2019
ms.locfileid: "64345712"
---
# <a name="compiler-error-c2085"></a>编译器错误 C2085

identifier： 不在形参列表中

函数定义中，但不是在形参列表中，已声明该标识符。 (仅适用于 ANSI C)

下面的示例生成 C2085:

```
// C2085.c
void func1( void )
int main( void ) {}   // C2085
```

可能的解决方法：

```
// C2085b.c
void func1( void );
int main( void ) {}
```

使用分号缺少`func1()`看起来像函数定义，而不是原型，因此`main`中定义`func1()`，标识符生成错误 C2085 `main`。