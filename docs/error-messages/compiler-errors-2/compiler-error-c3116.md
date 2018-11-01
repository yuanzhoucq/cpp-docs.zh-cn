---
title: 编译器错误 C3116
ms.date: 11/04/2016
f1_keywords:
- C3116
helpviewer_keywords:
- C3116
ms.assetid: 597463e1-a5cc-4ed3-a917-eae9a61d3312
ms.openlocfilehash: 3f587bc677d64bda0fb5eea0b7ebc8d5761a2e75
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50612010"
---
# <a name="compiler-error-c3116"></a>编译器错误 C3116

存储 specifier： 接口方法的存储类无效

所用`typedef`， `register`，或`static`为接口方法的存储类。 在接口成员上不允许这些存储类。

下面的示例生成 C3116:

```
// C3116.cpp
__interface ImyInterface
{
   static void myFunc();   // C3116
};
```