---
title: 编译器错误 C2101
ms.date: 11/04/2016
f1_keywords:
- C2101
helpviewer_keywords:
- C2101
ms.assetid: 42f0136f-8cc1-4f2b-be1c-721ec9278e66
ms.openlocfilehash: 8bea258bd3e20cba1dbfabdd3a669a44414b89f8
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74752335"
---
# <a name="compiler-error-c2101"></a>编译器错误 C2101

常量上的“&”

address-of 运算符 ( `&` ) 必须将左值作为操作数。

下面的示例生成 C2101：

```cpp
// C2101.cpp
int main() {
   char test;
   test = &'a';   // C2101
   test = 'a';   // OK
}
```
