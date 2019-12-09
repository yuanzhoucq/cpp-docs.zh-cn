---
title: 编译器错误 C2957
ms.date: 11/04/2016
f1_keywords:
- C2957
helpviewer_keywords:
- C2957
ms.assetid: 9cb4526f-4af8-47e9-b786-56192627ca72
ms.openlocfilehash: 122d6919271a165ceb0dad31a344e59cb3457a25
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74742764"
---
# <a name="compiler-error-c2957"></a>编译器错误 C2957

“delim”: 无效的左侧分隔符: 应为“<”

泛型类格式不正确。

下面的示例生成 C2957：

```cpp
// C2957.cpp
// compile with: /clr /LD
generic << class T>   // C2957
// try the following line instead
// generic < class T>
gc class C {};
```
