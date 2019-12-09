---
title: 编译器错误 C3896
ms.date: 11/04/2016
f1_keywords:
- C3896
helpviewer_keywords:
- C3896
ms.assetid: eb8be0f6-5b4e-4d71-8285-8a2a94f8ba29
ms.openlocfilehash: f15cd73465f4210ed5e5e34bebe2122c0b88f722
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74749264"
---
# <a name="compiler-error-c3896"></a>编译器错误 C3896

"member"：不正确的初始值设定项：此 literal 数据成员只能用 "nullptr" 进行初始化

[文本](../../extensions/literal-cpp-component-extensions.md)数据成员未正确初始化。  有关详细信息，请参阅[nullptr](../../extensions/nullptr-cpp-component-extensions.md) 。

下面的示例生成 C3896：

```cpp
// C3896.cpp
// compile with: /clr /c
ref class R{};

value class V {
   literal R ^ r = "test";   // C3896
   literal R ^ r2 = nullptr;   // OK
};
```
