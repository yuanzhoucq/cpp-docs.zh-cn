---
title: 编译器错误 C3896
ms.date: 11/04/2016
f1_keywords:
- C3896
helpviewer_keywords:
- C3896
ms.assetid: eb8be0f6-5b4e-4d71-8285-8a2a94f8ba29
ms.openlocfilehash: 00e103720dc666b17566b67da19d4e908bb3addd
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2019
ms.locfileid: "58767530"
---
# <a name="compiler-error-c3896"></a>编译器错误 C3896

member： 不正确的初始值设定项： 此 literal 数据成员只能初始化使用 nullptr

一个[文字](../../extensions/literal-cpp-component-extensions.md)数据成员未正确初始化。  请参阅[nullptr](../../extensions/nullptr-cpp-component-extensions.md)有关详细信息。

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