---
title: 编译器错误 C3880
ms.date: 11/04/2016
f1_keywords:
- C3880
helpviewer_keywords:
- C3880
ms.assetid: b0e05d1e-32d0-4034-9246-f37d23573ea9
ms.openlocfilehash: 60b96a9e704215ec1cbbab63eb77ca5d43ccb627
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50626936"
---
# <a name="compiler-error-c3880"></a>编译器错误 C3880

var： 不能是 literal 数据成员

类型[文字](../../windows/literal-cpp-component-extensions.md)属性必须为，或者编译时转换为，以下类型之一：

- 整型类型

- 字符串

- 具有整型或基础类型的枚举

下面的示例生成 C3880:

```
// C3880.cpp
// compile with: /clr /c
ref struct Y1 {
   literal System::Decimal staticConst1 = 10;   // C3880
   literal int staticConst2 = 10;   // OK
};
```