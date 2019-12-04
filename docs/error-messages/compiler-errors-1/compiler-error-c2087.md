---
title: 编译器错误 C2087
ms.date: 11/04/2016
f1_keywords:
- C2087
helpviewer_keywords:
- C2087
ms.assetid: 89761e83-415a-4468-a4c6-b6dedfd1dd6a
ms.openlocfilehash: 576ac394585b91f7c6ceadcdd07d25c639854990
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757899"
---
# <a name="compiler-error-c2087"></a>编译器错误 C2087

"identifier"：缺少下标

具有多个下标的数组的定义缺少维度大于1的下标值。

下面的示例生成 C2087：

```cpp
// C2087.cpp
int main() {
   char a[10][];   // C2087
}
```

可能的解决方法：

```cpp
// C2087b.cpp
int main() {
   char b[4][5];
}
```
