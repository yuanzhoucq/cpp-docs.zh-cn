---
title: 编译器警告（等级 1）C4939
ms.date: 11/04/2016
f1_keywords:
- C4939
helpviewer_keywords:
- C4939
ms.assetid: 07096008-ba47-436c-a84c-2b03ad90d0b3
ms.openlocfilehash: 00526b3dae5035fe96ec1abb50bbdd056ceecfaf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62408246"
---
# <a name="compiler-warning-level-1-c4939"></a>编译器警告（等级 1）C4939

\#pragma vtordisp 已弃用，将视觉对象的未来版本中删除C++

将从 Visual C++ 将来的版本中删除 [vtordisp](../../preprocessor/vtordisp.md) 杂注。

## <a name="example"></a>示例

下面的示例生成 C4939。

```
// C4939.cpp
// compile with: /c /W1
#pragma vtordisp(off)   // C4939
```