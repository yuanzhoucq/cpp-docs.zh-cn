---
title: 编译器警告（等级 1）C4215
ms.date: 11/04/2016
f1_keywords:
- C4215
helpviewer_keywords:
- C4215
ms.assetid: f2aab64d-1bab-4f75-95ee-89e1263047b1
ms.openlocfilehash: b62f382759c7e4c9dc888cf75d4df07a063df571
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199857"
---
# <a name="compiler-warning-level-1-c4215"></a>编译器警告（等级 1）C4215

使用了非标准扩展：长浮点

默认 Microsoft 扩展（/Ze）将**长浮点**视为**double**。 ANSI 兼容性（[/za](../../build/reference/za-ze-disable-language-extensions.md)）不会。 使用**double**维护兼容性。

下面的示例生成 C4215：

```cpp
// C4215.cpp
// compile with: /W1 /LD
long float a;   // C4215

// use the line below to resolve the warning
// double a;
```
