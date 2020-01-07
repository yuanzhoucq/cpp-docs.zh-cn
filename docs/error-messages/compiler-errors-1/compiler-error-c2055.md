---
title: 编译器错误 C2055
ms.date: 11/04/2016
f1_keywords:
- C2055
helpviewer_keywords:
- C2055
ms.assetid: 6cec79cc-6bec-443f-9897-fbf5452718c7
ms.openlocfilehash: 9cb6e4d5891c5aefc9d66e7d70a5cd7685ccd393
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/20/2019
ms.locfileid: "75302037"
---
# <a name="compiler-error-c2055"></a>编译器错误 C2055

应输入形参表，而不是类型列表

函数定义包含参数类型列表，而不包含形参列表。 ANSI C 要求使用形参命名，除非它们是 void 或省略号（`...`）。

下面的示例生成 C2055：

```c
// C2055.c
// compile with: /c
void func(int, char) {}  // C2055
void func (int i, char c) {}   // OK
```
