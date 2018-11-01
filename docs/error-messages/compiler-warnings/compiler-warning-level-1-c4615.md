---
title: 编译器警告（等级 1）C4615
ms.date: 11/04/2016
f1_keywords:
- C4615
helpviewer_keywords:
- C4615
ms.assetid: 7b107c01-0da2-4e01-8b40-93813e30b94c
ms.openlocfilehash: 1032261c39e0a285ac686e09573161de3b46e0e5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50573507"
---
# <a name="compiler-warning-level-1-c4615"></a>编译器警告（等级 1）C4615

\#杂注警告： 未知的用户警告类型

无效的警告说明符用于**杂注**[警告](../../preprocessor/warning.md)。 若要解决此错误，请使用有效的警告说明符。

下面的示例生成 C4615:

```
// C4615.cpp
// compile with: /W1 /LD
#pragma warning(enable : 4401)   // C4615, 'enable' not valid specifier

// use the code below to resolve the error
// #pragma warning(default : 4401)
```