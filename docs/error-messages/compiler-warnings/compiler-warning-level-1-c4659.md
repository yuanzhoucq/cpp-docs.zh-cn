---
title: 编译器警告 （等级 1） C4659 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4659
dev_langs:
- C++
helpviewer_keywords:
- C4659
ms.assetid: e29ba8db-7917-43f6-8e34-868b752279ae
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d00c54fa77d68722b2e47a9d49832911b398deca
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46110050"
---
# <a name="compiler-warning-level-1-c4659"></a>编译器警告（等级 1）C4659

\#杂注杂注： 行为未定义的保留段领域的使用，请使用 #pragma comment (linker，...)

.Drectve 选项用于将选项传递给链接器。 而是使用杂注[注释](../../preprocessor/comment-c-cpp.md)传递链接器选项。

```
// C4659.cpp
// compile with: /W1 /LD
#pragma code_seg(".drectve")   // C4659
```