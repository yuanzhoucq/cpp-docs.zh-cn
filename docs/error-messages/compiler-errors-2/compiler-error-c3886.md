---
title: 编译器错误 C3886
ms.date: 11/04/2016
f1_keywords:
- C3886
helpviewer_keywords:
- C3886
ms.assetid: 485f6c12-cc1b-4146-9034-409a0a5e615e
ms.openlocfilehash: 2e7ba0fcc76d723cebb5b82315faf36313b1d7db
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74736628"
---
# <a name="compiler-error-c3886"></a>编译器错误 C3886

"var"：必须初始化 literal 数据成员

在 declaraed[文本](../../extensions/literal-cpp-component-extensions.md)变量时，必须对其进行初始化。

下面的示例生成 C3886：

```cpp
// C3886.cpp
// compile with: /clr /c
ref struct Y1 {
   literal int staticConst;   // C3886
   literal int staticConst2 = 0;   // OK
};
```
