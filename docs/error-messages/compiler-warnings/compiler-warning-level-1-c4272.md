---
title: 编译器警告（等级 1）C4272
ms.date: 11/04/2016
f1_keywords:
- C4272
helpviewer_keywords:
- C4272
ms.assetid: 0d6c1de4-2eef-42c4-b861-c221f8b495ef
ms.openlocfilehash: 26e136aa395729d520f4a71a06b6dc212cf21f8b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62208306"
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