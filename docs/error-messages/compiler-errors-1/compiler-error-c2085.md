---
title: 编译器错误 C2085 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2085
dev_langs:
- C++
helpviewer_keywords:
- C2085
ms.assetid: 0a86785c-8e6f-481b-8c7b-412220c1950d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d88968e49e38a13782dde2d905a614ad4d177e81
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46082373"
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