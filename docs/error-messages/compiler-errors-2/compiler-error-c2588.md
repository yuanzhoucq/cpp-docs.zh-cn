---
title: 编译器错误 C2588
ms.date: 11/04/2016
f1_keywords:
- C2588
helpviewer_keywords:
- C2588
ms.assetid: 19a0cabd-ca13-44a5-9be3-ee676abf9bc4
ms.openlocfilehash: f1f73e2585606e7e86213607a96ef713345419c1
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755403"
---
# <a name="compiler-error-c2588"></a>编译器错误 C2588

"：： ~ identifier"：非法的全局析构函数

析构函数是为类、结构或联合以外的对象定义的。 不允许这样做。

如果作用域解析（`::`）运算符左侧缺少类、结构或联合名称，则会导致此错误。

下面的示例生成 C2588：

```cpp
// C2588.cpp
~F();   // C2588
```
