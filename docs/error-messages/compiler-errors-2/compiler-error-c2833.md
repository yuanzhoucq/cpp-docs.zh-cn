---
title: 编译器错误 C2833
ms.date: 11/04/2016
f1_keywords:
- C2833
helpviewer_keywords:
- C2833
ms.assetid: b9418ce1-e2ee-4599-8959-6fde89c27569
ms.openlocfilehash: a6ffcb13d04f3c7c5ac62e147a2b6b2b305e11e1
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218164"
---
# <a name="compiler-error-c2833"></a>编译器错误 C2833

> "operator *operator-name*" 不是可识别的运算符或类型

该单词 **`operator`** 必须后跟要重写的*运算符名称*或要转换的类型。

有关可以在托管类型中定义的运算符的列表，请参阅[用户定义的运算符](../../dotnet/user-defined-operators-cpp-cli.md)。

下面的示例生成 C2833：

```cpp
// C2833.cpp
// compile with: /c
class A {};

void operator ::* ();   // C2833
void operator :: ();   // OK
```
