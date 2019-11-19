---
title: 编译器警告（等级1） C4508
ms.date: 11/04/2016
f1_keywords:
- C4508
helpviewer_keywords:
- C4508
ms.assetid: c05f113b-b789-4df0-a4ef-78bce4767021
ms.openlocfilehash: 394a59a472100cc30476b5bb87f30c45d867f94b
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966295"
---
# <a name="compiler-warning-level-1-c4508"></a>编译器警告（等级1） C4508

"function"：函数应返回值;假定为 "void" 返回类型

函数没有指定的返回类型。 在这种情况下，还应激发 C4430，并由编译器实现 C4430 报告的修复（默认值为 int）。

若要解决此警告，请显式声明函数的返回类型。

下面的示例生成 C4508：

```cpp
// C4508.cpp
// compile with: /W1 /c
#pragma warning (disable : 4430)
func() {}   // C4508
void func2() {}   // OK
```