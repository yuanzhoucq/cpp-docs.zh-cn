---
title: 编译器错误 C2534
ms.date: 11/04/2016
f1_keywords:
- C2534
helpviewer_keywords:
- C2534
ms.assetid: 481f9f54-5b51-4aa0-8eea-218f10807705
ms.openlocfilehash: e684804ea31b16f31c82e244cb4f9a6aaf2d08c3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62386962"
---
# <a name="compiler-error-c2534"></a>编译器错误 C2534

identifier： 构造函数无法返回值

构造函数不能返回值或具有返回类型 (甚至不能`void`返回类型)。

通过删除可能会修复此错误`return`从构造函数定义的语句。

下面的示例生成 C2534:

```
// C2534.cpp
class A {
public:
   int i;
   A() { return i; }   // C2534
};
```