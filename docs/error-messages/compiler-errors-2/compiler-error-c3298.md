---
title: 编译器错误 C3298
ms.date: 11/04/2016
f1_keywords:
- C3298
helpviewer_keywords:
- C3298
ms.assetid: 458c2680-95bb-4d5e-895f-ce4115844193
ms.openlocfilehash: fe6913d402c6ce4df3551c159eb56a12590799cb
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59779123"
---
# <a name="compiler-error-c3298"></a>编译器错误 C3298

“constraint_1”：不能使用“constraint_2”作为约束，因为“constraint_2”具有 ref 约束，而“constraint_1”具有值约束

不能为约束指定相互排斥的特征。 例如，不能同时将泛型类型参数约束为值类型和引用类型。

有关详细信息，请参阅[泛型类型参数的约束 (C++/CLI)](../../extensions/constraints-on-generic-type-parameters-cpp-cli.md)。

## <a name="example"></a>示例

下面的示例生成 C3298。

```
// C3298.cpp
// compile with: /clr /c
generic<class T, class U>
where T : ref class
where U : T, value class   // C3298
public ref struct R {};
```