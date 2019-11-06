---
title: 编译器警告（等级 1）C4087
ms.date: 11/04/2016
f1_keywords:
- C4087
helpviewer_keywords:
- C4087
ms.assetid: 546e4d57-5c8e-422c-8ef1-92657336dad5
ms.openlocfilehash: fe2b4fadfb87726e81178a3530299dbb8620aec9
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626842"
---
# <a name="compiler-warning-level-1-c4087"></a>编译器警告（等级 1）C4087

“function”：用“void”参数列表声明

函数声明没有形参，而函数调用具有实参。 根据该函数的调用约定传递了额外的参数。

此警告针对 C 编译器。

## <a name="example"></a>示例

```c
// C4087.c
// compile with: /W1
int f1( void ) {
}

int main() {
   f1( 10 );   // C4087
}
```