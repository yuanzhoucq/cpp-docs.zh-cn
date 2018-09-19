---
title: 编译器警告 （等级 1） C4939 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4939
dev_langs:
- C++
helpviewer_keywords:
- C4939
ms.assetid: 07096008-ba47-436c-a84c-2b03ad90d0b3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6e13cab2d5277cca0a1962b8ec254aaef10cfc98
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46118760"
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