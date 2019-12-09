---
title: 编译器错误 C2499
ms.date: 11/04/2016
f1_keywords:
- C2499
helpviewer_keywords:
- C2499
ms.assetid: b323ff4d-b3c1-4bfd-b052-ae7292d53222
ms.openlocfilehash: 29fbb691304f9fc101f2367e014ae1e4e2231ff0
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756976"
---
# <a name="compiler-error-c2499"></a>编译器错误 C2499

"class"：类不能是其自身的基类

您尝试指定要定义为基类的类。

下面的示例生成 C2499：

```cpp
// C2499.cpp
// compile with: /c
class CMyClass : public CMyClass {};   // C2499
class CMyClass{};   // OK
```
