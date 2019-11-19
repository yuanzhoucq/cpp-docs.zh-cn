---
title: 编译器警告（等级1） C4172
ms.date: 11/04/2016
f1_keywords:
- C4172
helpviewer_keywords:
- C4172
ms.assetid: a8d2bf65-d8b1-4fe3-8340-a223d7e7fde6
ms.openlocfilehash: 7d53972dbcb2e3ab6a95b0b874cc6bb98cd66840
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/05/2019
ms.locfileid: "73624829"
---
# <a name="compiler-warning-level-1-c4172"></a>编译器警告（等级1） C4172

返回局部变量或临时变量的地址

函数返回局部变量或临时对象的地址。 当函数返回时，局部变量和临时对象将被销毁，因此返回的地址无效。

重新设计函数，使其不返回本地对象的地址。

下面的示例生成 C4172：

```cpp
// C4172.cpp
// compile with: /W1 /LD
float f = 10;

const double& bar() {
// try the following line instead
// const float& bar() {
   return f;   // C4172
}
```