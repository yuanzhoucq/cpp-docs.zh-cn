---
title: 编译器警告（等级 1）C4939
ms.date: 11/04/2016
f1_keywords:
- C4939
helpviewer_keywords:
- C4939
ms.assetid: 07096008-ba47-436c-a84c-2b03ad90d0b3
ms.openlocfilehash: 5c87dad744281464599ee6c28b5bcf6e350b9feb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199272"
---
# <a name="compiler-warning-level-1-c4939"></a>编译器警告（等级 1）C4939

\#杂注 vtordisp 已弃用，并将在 Visual 的未来版本中删除C++

将从 Visual C++ 将来的版本中删除 [vtordisp](../../preprocessor/vtordisp.md) 杂注。

## <a name="example"></a>示例

下面的示例生成 C4939。

```cpp
// C4939.cpp
// compile with: /c /W1
#pragma vtordisp(off)   // C4939
```
