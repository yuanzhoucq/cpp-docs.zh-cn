---
title: 编译器错误 C3816
ms.date: 11/04/2016
f1_keywords:
- C3816
helpviewer_keywords:
- C3816
ms.assetid: 2e52cc7f-e31c-41a3-8d6f-9f5fab3648c0
ms.openlocfilehash: 5e31138d50676c312028e35b480cc682dc146a43
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757119"
---
# <a name="compiler-error-c3816"></a>编译器错误 C3816

"声明" 以前是用不同的托管或 WinRTmodifier 声明或定义的

前向声明和实际声明要求特性声明中不存在任何冲突或不一致。

下面的示例生成 C3816，并演示如何修复此错误：

```cpp
// C3816a.cpp
// compile with: /clr /c
class C1;
// try the following line instead
// ref class C1;

ref class C1{  // C3816, forward declaration does not use ref
};
```
