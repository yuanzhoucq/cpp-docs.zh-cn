---
title: 编译器警告（等级 1）C4939
ms.date: 11/04/2016
f1_keywords:
- C4939
helpviewer_keywords:
- C4939
ms.assetid: 07096008-ba47-436c-a84c-2b03ad90d0b3
ms.openlocfilehash: 00526b3dae5035fe96ec1abb50bbdd056ceecfaf
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50538524"
---
# <a name="compiler-warning-level-1-c4939"></a>编译器警告（等级 1）C4939

\#杂注 vtordisp 已弃用，并将 Visual c + + 的未来版本中删除

将从 Visual C++ 将来的版本中删除 [vtordisp](../../preprocessor/vtordisp.md) 杂注。

## <a name="example"></a>示例

下面的示例生成 C4939。

```
// C4939.cpp
// compile with: /c /W1
#pragma vtordisp(off)   // C4939
```