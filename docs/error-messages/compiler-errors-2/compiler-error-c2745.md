---
title: 编译器错误 C2745
ms.date: 11/04/2016
f1_keywords:
- C2745
helpviewer_keywords:
- C2745
ms.assetid: a1c45f13-7667-4678-aa16-265304a449a1
ms.openlocfilehash: 5fe19bcf55c743bb3e35d1ca9ae28d2b08dcbd89
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759004"
---
# <a name="compiler-error-c2745"></a>编译器错误 C2745

"token"：此标记不能转换为标识符

标识符必须包含合法字符。

下面的示例生成 C2745：

```cpp
// C2745.cpp
// compile with: /clr
int main() {
   int __identifier([));   // C2745
}
```
