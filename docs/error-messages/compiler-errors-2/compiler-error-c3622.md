---
title: 编译器错误 C3622
ms.date: 11/04/2016
f1_keywords:
- C3622
helpviewer_keywords:
- C3622
ms.assetid: 02836f78-0cf2-4947-b87e-710187d81014
ms.openlocfilehash: ed307f46db1261d79d5b0ec6b36852cac2e6d13e
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59776114"
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
