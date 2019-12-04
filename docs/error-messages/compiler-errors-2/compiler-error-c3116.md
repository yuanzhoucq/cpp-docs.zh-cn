---
title: 编译器错误 C3116
ms.date: 11/04/2016
f1_keywords:
- C3116
helpviewer_keywords:
- C3116
ms.assetid: 597463e1-a5cc-4ed3-a917-eae9a61d3312
ms.openlocfilehash: d0c8e7cab936171f89b33c90b4134a97c40b2c81
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74741178"
---
# <a name="compiler-error-c3116"></a>编译器错误 C3116

"存储说明符"：接口方法的存储类无效

你使用 `typedef`、`register`或 `static` 作为接口方法的存储类。 这些存储类在接口成员上不允许。

下面的示例生成 C3116：

```cpp
// C3116.cpp
__interface ImyInterface
{
   static void myFunc();   // C3116
};
```
