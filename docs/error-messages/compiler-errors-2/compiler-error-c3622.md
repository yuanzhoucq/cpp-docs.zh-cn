---
title: 编译器错误 C3622
ms.date: 11/04/2016
f1_keywords:
- C3622
helpviewer_keywords:
- C3622
ms.assetid: 02836f78-0cf2-4947-b87e-710187d81014
ms.openlocfilehash: 2adcee4cb20c39c39b06e0ac2087478cfe2d8937
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74740892"
---
# <a name="compiler-error-c3622"></a>编译器错误 C3622

"class"：声明为 "关键字" 的类不能实例化

尝试实例化标记为[抽象](../../extensions/abstract-cpp-component-extensions.md)的类。 标记为 `abstract` 的类可以是基类，但不能进行实例化。

## <a name="example"></a>示例

下面的示例生成 C3622。

```cpp
// C3622.cpp
// compile with: /clr
ref class a abstract {};

int main() {
   a aa;   // C3622
}
```
