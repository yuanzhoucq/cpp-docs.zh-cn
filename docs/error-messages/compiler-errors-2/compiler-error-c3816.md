---
title: 编译器错误 C3816
ms.date: 11/04/2016
f1_keywords:
- C3816
helpviewer_keywords:
- C3816
ms.assetid: 2e52cc7f-e31c-41a3-8d6f-9f5fab3648c0
ms.openlocfilehash: d362480b3380fe4576ef56b8ca76dfa10eaa1408
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50557295"
---
# <a name="compiler-error-c3816"></a>编译器错误 C3816

declaration 以前声明或定义与不同的托管或 WinRTmodifier

前向声明和实际声明要求特性声明中不存在任何冲突或不一致。

下面的示例生成 C3816，并演示如何修复此错误：

```
// C3816a.cpp
// compile with: /clr /c
class C1;
// try the following line instead
// ref class C1;

ref class C1{  // C3816, forward declaration does not use ref
};
```