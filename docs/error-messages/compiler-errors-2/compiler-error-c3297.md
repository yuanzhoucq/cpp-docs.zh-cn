---
title: 编译器错误 C3297 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3297
dev_langs:
- C++
helpviewer_keywords:
- C3297
ms.assetid: 2a718b4c-6cdb-4418-92c0-fc3a259431c4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7aa23cebc7ad7019c375c351f723b7ad1573ab86
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46069828"
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