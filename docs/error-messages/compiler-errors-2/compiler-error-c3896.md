---
title: 编译器错误 C3896 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3896
dev_langs:
- C++
helpviewer_keywords:
- C3896
ms.assetid: eb8be0f6-5b4e-4d71-8285-8a2a94f8ba29
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6714d356fa2f09bdfce2750ff31432b5b4e14461
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46109725"
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