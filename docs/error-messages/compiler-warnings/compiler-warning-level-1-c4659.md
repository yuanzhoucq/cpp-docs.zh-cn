---
title: 编译器警告（等级 1）C4659
ms.date: 11/04/2016
f1_keywords:
- C4659
helpviewer_keywords:
- C4659
ms.assetid: e29ba8db-7917-43f6-8e34-868b752279ae
ms.openlocfilehash: 1766cb285fa33d384d57e89c7243fc35022ae006
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175631"
---
# <a name="compiler-warning-level-1-c4659"></a>编译器警告（等级 1）C4659

\#杂注 "pragma"：保留段 "segment" 的使用具有未定义的行为，请使用 #pragma 注释（链接器 ...）

使用 .drectve 选项将选项传递到链接器。 改为使用杂注[注释](../../preprocessor/comment-c-cpp.md)传递链接器选项。

```cpp
// C4659.cpp
// compile with: /W1 /LD
#pragma code_seg(".drectve")   // C4659
```
