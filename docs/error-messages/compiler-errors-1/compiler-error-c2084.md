---
title: 编译器错误 C2084
ms.date: 11/04/2016
f1_keywords:
- C2084
helpviewer_keywords:
- C2084
ms.assetid: 990b107f-3721-4851-ae8b-4b69a8c149ed
ms.openlocfilehash: f217e0b94e27c0f85879e80b3ae887cb4f76f486
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216357"
---
# <a name="compiler-error-c2084"></a>编译器错误 C2084

函数 "*function*" 已经有一个主体

已定义该函数。

在 Visual Studio 2002 之前，

- 编译器将接受解析为同一实际类型的多个模板专用化，但其他定义绝不会可用。 编译器现在会检测这些多个定义。

- **`__int32`** 和被 **`int`** 视为不同的类型。 编译器现在将视为 **`__int32`** 的同义词 **`int`** 。 这意味着，如果函数在和上重载，则编译器将检测多个定义 **`__int32`** **`int`** 并提供错误。

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
