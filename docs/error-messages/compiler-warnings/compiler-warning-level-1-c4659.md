---
title: 编译器警告（等级1） C4659
ms.date: 11/04/2016
f1_keywords:
- C4659
helpviewer_keywords:
- C4659
ms.assetid: e29ba8db-7917-43f6-8e34-868b752279ae
ms.openlocfilehash: 27023e6886638be63db1e1fb654c0caa70769a56
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052534"
---
# <a name="compiler-warning-level-1-c4659"></a>编译器警告（等级1） C4659

\#杂注 "pragma"：保留段 "segment" 的使用具有未定义的行为，请使用 #pragma 注释（链接器 ...）

使用 .drectve 选项将选项传递到链接器。 改为使用杂注[注释](../../preprocessor/comment-c-cpp.md)传递链接器选项。

```cpp
// C4659.cpp
// compile with: /W1 /LD
#pragma code_seg(".drectve")   // C4659
```