---
title: 编译器错误 C2084
ms.date: 11/04/2016
f1_keywords:
- C2084
helpviewer_keywords:
- C2084
ms.assetid: 990b107f-3721-4851-ae8b-4b69a8c149ed
ms.openlocfilehash: 881ae051b2779fe674b31b64a7cbe7be7cf63705
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757886"
---
# <a name="compiler-error-c2084"></a>编译器错误 C2084

函数 "*function*" 已经有一个主体

已定义该函数。

在 Visual Studio 2002 之前，

- 编译器将接受解析为同一实际类型的多个模板专用化，但其他定义绝不会可用。 编译器现在会检测这些多个定义。

- `__int32` 和 `int` 被视为不同的类型。 编译器现在将 `__int32` 视为 `int`的同义词。 这意味着，如果函数在 `__int32` 和 `int` 上都重载，编译器将检测多个定义并提供错误。

## <a name="example"></a>示例

下面的示例生成 C2084：

```cpp
// C2084.cpp
void Func(int);
void Func(int) {}   // define function
void Func(int) {}   // C2084 second definition
```

若要更正此错误，请删除重复的定义：

```cpp
// C2084b.cpp
// compile with: /c
void Func(int);
void Func(int) {}
```
