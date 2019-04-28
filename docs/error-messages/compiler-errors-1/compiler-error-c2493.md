---
title: 编译器错误 C2493
ms.date: 11/04/2016
f1_keywords:
- C2493
helpviewer_keywords:
- C2493
ms.assetid: 68316cd5-682b-49c3-b6ea-23c4e5d296cf
ms.openlocfilehash: d5e64b2586803f7463582710721d2cb5c0eac200
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62360861"
---
# <a name="compiler-error-c2493"></a>编译器错误 C2493

__based 的非法窗体

一个`__based`表达式必须基于指针。

下面的示例生成 C2493:

```
// C2493.cpp
// compile with: /c
char mybase;
int __based(mybase) ptr;   // C2493

// OK
char * mybase;
int __based(mybase) * ptr;
```