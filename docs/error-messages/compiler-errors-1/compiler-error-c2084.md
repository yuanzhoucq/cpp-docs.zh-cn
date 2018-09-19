---
title: 编译器错误 C2084 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2084
dev_langs:
- C++
helpviewer_keywords:
- C2084
ms.assetid: 990b107f-3721-4851-ae8b-4b69a8c149ed
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 09ce703b6908257e37c2b7ff1b2714f1426f941f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46052098"
---
# <a name="compiler-error-c2084"></a>编译器错误 C2084

函数*函数*已具有一个主体

已定义的函数。

在 Visual Studio 2002 年之前, 的 Visual c + + 的版本

- 尽管将永远不能附加的定义，编译器会接受解析为相同的实际类型的多个模板专用化。 现在，编译器检测到这些多个定义。

- `__int32` 和`int`被视为单独的类型。 编译器现在将`__int32`的同义词`int`。 这意味着，编译器检测到多个定义如果函数重载上都`__int32`和`int`并显示错误。

## <a name="example"></a>示例

下面的示例生成 C2084:

```cpp
// C2084.cpp
void Func(int);
void Func(int) {}   // define function
void Func(int) {}   // C2084 second definition
```

若要更正此错误，请删除重复的定义：

```
// C2084b.cpp
// compile with: /c
void Func(int);
void Func(int) {}
```