---
title: 编译器错误 C2833
ms.date: 11/04/2016
f1_keywords:
- C2833
helpviewer_keywords:
- C2833
ms.assetid: b9418ce1-e2ee-4599-8959-6fde89c27569
ms.openlocfilehash: c1467a3c67cccf28cc6b9bd0f987fe77b8da8988
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757873"
---
# <a name="compiler-error-c2833"></a>编译器错误 C2833

"operator operator" 不是可识别的运算符或类型

单词 `operator` 必须后跟要重写的运算符或要转换的类型。

有关可以在托管类型中定义的运算符的列表，请参阅[用户定义的运算符](../../dotnet/user-defined-operators-cpp-cli.md)。

下面的示例生成 C2833：

```cpp
// C2833.cpp
// compile with: /c
class A {};

void operator ::* ();   // C2833
void operator :: ();   // OK
```
