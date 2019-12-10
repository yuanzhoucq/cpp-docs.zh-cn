---
title: 编译器警告（等级 4）C4918
ms.date: 11/04/2016
f1_keywords:
- C4918
helpviewer_keywords:
- C4918
ms.assetid: 1bcf6d35-3467-4aa8-b2ef-cb33f4e70238
ms.openlocfilehash: 801c22a45037492dc609d93c6339ab8feff30494
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988804"
---
# <a name="compiler-warning-level-4-c4918"></a>编译器警告（等级 4）C4918

“character”: 杂注优化列表中的无效字符

在 [optimize](../../preprocessor/optimize.md) 杂注语句的优化列表中发现未知字符。

例如，以下语句生成 C4918：

```cpp
// C4918.cpp
// compile with: /W4
#pragma optimize("X", on) // C4918 expected
int main()
{
}
```
