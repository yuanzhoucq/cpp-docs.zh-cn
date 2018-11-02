---
title: 编译器错误 C2663
ms.date: 11/04/2016
f1_keywords:
- C2663
helpviewer_keywords:
- C2663
ms.assetid: 1e93e368-fd52-42bf-9908-9b6df467c8c9
ms.openlocfilehash: d74326e49edd980896276e2c6e67526d8d769cb7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50644335"
---
# <a name="compiler-error-c2663"></a>编译器错误 C2663

function： 数字重载具有 this 指针没有合法转换

编译器无法将转换`this`到任何成员函数的重载版本。

此错误可能由调用非`const`成员函数上的`const`对象。  可能的解决方法：

1. 删除`const`从对象声明。

1. 添加`const`成员函数重载之一。

下面的示例生成 C2663:

```
// C2663.cpp
struct C {
   void f() volatile {}
   void f() {}
};

struct D {
   void f() volatile;
   void f() const {}
};

const C *pcc;
const D *pcd;

int main() {
   pcc->f();    // C2663
   pcd->f();    // OK
}
```