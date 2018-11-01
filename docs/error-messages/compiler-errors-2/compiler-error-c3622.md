---
title: 编译器错误 C3622
ms.date: 11/04/2016
f1_keywords:
- C3622
helpviewer_keywords:
- C3622
ms.assetid: 02836f78-0cf2-4947-b87e-710187d81014
ms.openlocfilehash: 69565a1a2d159623bca927a94543834d18c13299
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50518087"
---
# <a name="compiler-error-c3622"></a>编译器错误 C3622

class： 类声明为 keyword 不能实例化

尝试实例化类标记为[抽象](../../windows/abstract-cpp-component-extensions.md)。 一个类标记为`abstract`可以是基类，但它不能实例化。

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
