---
title: 编译器错误 C2874
ms.date: 11/04/2016
f1_keywords:
- C2874
helpviewer_keywords:
- C2874
ms.assetid: b54fa9d8-8df5-40d9-9b3b-aa3e9dd6a3be
ms.openlocfilehash: a54cb9dda4ae07ea274eaa970248b9ce9002693b
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74736368"
---
# <a name="compiler-error-c2874"></a>编译器错误 C2874

using 声明导致 "symbol" 的多个声明

声明导致同一项被定义了两次。

下面的示例生成 C2874：

```cpp
// C2874.cpp
namespace Z {
   int i;
}

int main() {
   int i;
   using Z::i;   // C2874, i already declared
}
```
