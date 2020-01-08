---
title: 编译器错误 C2054
ms.date: 11/04/2016
f1_keywords:
- C2054
helpviewer_keywords:
- C2054
ms.assetid: 37f7c612-0d7d-4728-9e67-ac4160555f48
ms.openlocfilehash: e7d90d684c1d95f540f6357bf61ee7c6f889ad3f
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/20/2019
ms.locfileid: "75302050"
---
# <a name="compiler-error-c2054"></a>编译器错误 C2054

应输入 "（" 跟随 "identifier"

函数标识符用于需要尾随括号的上下文中。

此错误的原因可能是省略了复杂初始化上的等号（=）。

下面的示例生成 C2054：

```c
// C2054.c
int array1[] { 1, 2, 3 };   // C2054, missing =
```

可能的解决方法：

```c
// C2054b.c
int main() {
   int array2[] = { 1, 2, 3 };
}
```
