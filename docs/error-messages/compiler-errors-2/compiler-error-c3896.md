---
title: 编译器错误 C3896
ms.date: 11/04/2016
f1_keywords:
- C3896
helpviewer_keywords:
- C3896
ms.assetid: eb8be0f6-5b4e-4d71-8285-8a2a94f8ba29
ms.openlocfilehash: 32aed1dfd957035cdd60fa97bd9ec534de03cb06
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50547926"
---
# <a name="compiler-error-c3896"></a>编译器错误 C3896

member： 不正确的初始值设定项： 此 literal 数据成员只能初始化使用 nullptr

一个[文字](../../windows/literal-cpp-component-extensions.md)数据成员未正确初始化。  请参阅[nullptr](../../windows/nullptr-cpp-component-extensions.md)有关详细信息。

下面的示例生成 C3896:

```
// C3896.cpp
// compile with: /clr /c
ref class R{};

value class V {
   literal R ^ r = "test";   // C3896
   literal R ^ r2 = nullptr;   // OK
};
```