---
title: 编译器警告（等级 1）C4272
ms.date: 11/04/2016
f1_keywords:
- C4272
helpviewer_keywords:
- C4272
ms.assetid: 0d6c1de4-2eef-42c4-b861-c221f8b495ef
ms.openlocfilehash: 747b9e60ad2b8b0036c6eac50d44c2d70277384f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80163120"
---
# <a name="compiler-warning-level-1-c4272"></a>编译器警告（等级 1）C4272

"function"：标记 __declspec （dllimport）;导入函数时必须指定本机调用约定。

导出使用[__clrcall](../../cpp/clrcall.md)调用约定标记的函数是错误的，如果尝试导入标记为 `__clrcall`的函数，编译器会发出此警告。

下面的示例生成 C4272：

```cpp
// C4272.cpp
// compile with: /c /W1 /clr
__declspec(dllimport) void __clrcall Test();   // C4272
__declspec(dllimport) void Test2();   // OK
```
