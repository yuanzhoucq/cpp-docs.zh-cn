---
title: 编译器错误 C2428
ms.date: 11/04/2016
f1_keywords:
- C2428
helpviewer_keywords:
- C2428
ms.assetid: 74aa5714-e930-4f9e-9061-68ccce7f0d38
ms.openlocfilehash: 2a85e1874a03882ca8497eeff379d377a585fe06
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216227"
---
# <a name="compiler-error-c2428"></a>编译器错误 C2428

"operation"：在 "bool" 类型的操作数上不允许

不能将减量运算符应用于类型的对象 **`bool`** 。

下面的示例生成 C2428：

```cpp
// C2428.cpp
void g(bool fFlag) {
   --fFlag;   // C2428
   fFlag--;   // C2428
}
```
