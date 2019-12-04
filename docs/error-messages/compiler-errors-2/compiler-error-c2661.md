---
title: 编译器错误 C2661
ms.date: 11/04/2016
f1_keywords:
- C2661
helpviewer_keywords:
- C2661
ms.assetid: 60021467-71cd-451b-9877-23840c69309f
ms.openlocfilehash: e4d0e8a1c707374e0e93a5687351a9360fa17c0f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756040"
---
# <a name="compiler-error-c2661"></a>编译器错误 C2661

"function"：没有重载函数使用数字参数

可能的原因：

1. 函数调用中的实参不正确。

1. 缺少函数声明。

下面的示例生成 C2661：

```cpp
// C2661.cpp
void func( int ){}
void func( int, int ){}
int main() {
   func( );   // C2661 func( void ) was not declared
   func( 1 );   // OK func( int ) was declared
}
```
