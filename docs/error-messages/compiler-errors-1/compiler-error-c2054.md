---
title: 编译器错误 C2054
ms.date: 11/04/2016
f1_keywords:
- C2054
helpviewer_keywords:
- C2054
ms.assetid: 37f7c612-0d7d-4728-9e67-ac4160555f48
ms.openlocfilehash: 7366995f8930b4733ccff73aef38ebcf65a0c120
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50575651"
---
# <a name="compiler-error-c2054"></a>编译器错误 C2054

预期 ' (' 遵循 identifier

需要使用尾随括号的上下文中使用函数标识符。

可以通过省略等号 （=） 在复杂的初始化导致此错误。

下面的示例生成 C2054:

```
// C2054.c
int array1[] { 1, 2, 3 };   // C2054, missing =
```

可能的解决方法：

```
// C2054b.c
int main() {
   int array2[] = { 1, 2, 3 };
}
```