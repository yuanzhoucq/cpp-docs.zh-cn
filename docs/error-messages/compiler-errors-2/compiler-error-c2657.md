---
title: 编译器错误 C2657
ms.date: 11/04/2016
f1_keywords:
- C2657
helpviewer_keywords:
- C2657
ms.assetid: f7cf29a9-684a-4605-9469-ecfee9ba4b03
ms.openlocfilehash: 4e2816092b3c0c210ae2c544e9bf9a823a9c5d18
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50661131"
---
# <a name="compiler-error-c2657"></a>编译器错误 C2657

类:: * 语句的开始找到 （是否忘记指定类型？）

在行开头的指针到成员标识符。

此错误可能被引起给成员的指针的声明中缺少类型说明符。

下面的示例生成 C2657:

```
// C2657.cpp
class C {};
int main() {
   C::* pmc1;        // C2657
   int C::* pmc2;   // OK
}
```