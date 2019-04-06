---
title: 编译器错误 C3622
ms.date: 11/04/2016
f1_keywords:
- C3622
helpviewer_keywords:
- C3622
ms.assetid: 02836f78-0cf2-4947-b87e-710187d81014
ms.openlocfilehash: ed307f46db1261d79d5b0ec6b36852cac2e6d13e
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "58781908"
---
# <a name="compiler-error-c3622"></a>编译器错误 C3622

class： 类声明为 keyword 不能实例化

尝试实例化类标记为[抽象](../../extensions/abstract-cpp-component-extensions.md)。 一个类标记为`abstract`可以是基类，但它不能实例化。

## <a name="example"></a>示例

下面的示例生成 C3622。

```
// C3622.cpp
// compile with: /clr
ref class a abstract {};

int main() {
   a aa;   // C3622
}
```
