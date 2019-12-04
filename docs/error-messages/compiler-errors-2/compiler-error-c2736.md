---
title: 编译器错误 C2736
ms.date: 11/04/2016
f1_keywords:
- C2736
helpviewer_keywords:
- C2736
ms.assetid: 95a6bc28-c0cb-49dc-87e6-e993dbbba881
ms.openlocfilehash: 6a7781ebcd7cefdbcff13599912c06062f20501e
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759680"
---
# <a name="compiler-error-c2736"></a>编译器错误 C2736

不允许在强制转换中使用 "关键字" 关键字

关键字在强制转换中无效。

下面的示例生成 C2736：

```cpp
// C2736.cpp
int main() {
   return (virtual) 0;   // C2736
   // try the following line instead
   // return 0;
}
```
