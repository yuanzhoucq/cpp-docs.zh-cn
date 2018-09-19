---
title: 编译器警告 （等级 1） C4272 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4272
dev_langs:
- C++
helpviewer_keywords:
- C4272
ms.assetid: 0d6c1de4-2eef-42c4-b861-c221f8b495ef
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 00e30646c9fe56132da9cf87ba71cb54ae6a3e8f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46052954"
---
# <a name="compiler-warning-level-1-c4272"></a>编译器警告（等级 1）C4272

function： 被标记为 __declspec （dllimport）;导入函数时，必须指定本机调用约定。

它是导出函数标记为错误[__clrcall](../../cpp/clrcall.md)如果你尝试导入标记的函数调用约定和编译器发出此警告`__clrcall`。

下面的示例生成 C4272:

```
// C4272.cpp
// compile with: /c /W1 /clr
__declspec(dllimport) void __clrcall Test();   // C4272
__declspec(dllimport) void Test2();   // OK
```