---
title: 编译器警告（等级1） C4272
ms.date: 11/04/2016
f1_keywords:
- C4272
helpviewer_keywords:
- C4272
ms.assetid: 0d6c1de4-2eef-42c4-b861-c221f8b495ef
ms.openlocfilehash: 13c56c2261cd069e7edec63921c198e2bee56c95
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626699"
---
# <a name="compiler-warning-level-1-c4272"></a>编译器警告（等级1） C4272

"function"：标记为 __declspec （dllimport）;导入函数时必须指定本机调用约定。

导出使用[__clrcall](../../cpp/clrcall.md)调用约定标记的函数是错误的，如果尝试导入标记为 `__clrcall`的函数，编译器会发出此警告。

下面的示例生成 C4272：

```cpp
// C4272.cpp
// compile with: /c /W1 /clr
__declspec(dllimport) void __clrcall Test();   // C4272
__declspec(dllimport) void Test2();   // OK
```