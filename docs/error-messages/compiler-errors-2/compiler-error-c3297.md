---
title: 编译器错误 C3297
ms.date: 11/04/2016
f1_keywords:
- C3297
helpviewer_keywords:
- C3297
ms.assetid: 2a718b4c-6cdb-4418-92c0-fc3a259431c4
ms.openlocfilehash: 6df8fd3df023602f65c872dedd74da36bbbc6bd8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50649912"
---
# <a name="compiler-error-c3297"></a>编译器错误 C3297

“constraint_2”：不能使用“constraint_1”作为约束，因为“constraint_1”具有值约束

值类已密封。 如果约束是值类，则永远无法从它派生其他约束。

有关详细信息，请参阅[泛型类型参数的约束 (C + + CLI)](../../windows/constraints-on-generic-type-parameters-cpp-cli.md)。

## <a name="example"></a>示例

下面的示例生成 C3297。

```
// C3297.cpp
// compile with: /clr /c
generic<class T, class U>
where T : value class
where U : T   // C3297
public ref struct R {};
```