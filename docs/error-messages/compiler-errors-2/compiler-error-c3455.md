---
title: 编译器错误 C3455
ms.date: 11/04/2016
f1_keywords:
- C3455
helpviewer_keywords:
- C3455
ms.assetid: 218e5cfe-5391-4eeb-81c2-85c47e3a6cd2
ms.openlocfilehash: 4451ddbd8d5a7125112ef8e1c58e8843095bffd4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50614391"
---
# <a name="compiler-error-c3455"></a>编译器错误 C3455

“attribute”：没有任何特性构造函数匹配这些参数

已使用无效的值声明特性。  有关更多信息，请参见 [attribute](../../windows/attributes/attribute.md) 。

## <a name="example"></a>示例

以下示例生成 C3455

```
// C3455.cpp
// compile with: /clr /c
using namespace System;

[attribute("MyAt")]   // C3455
// try the following line instead
// [attribute(All)]
ref struct MyAttr {
   MyAttr() {}
};
```