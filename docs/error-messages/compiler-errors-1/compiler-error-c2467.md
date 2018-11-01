---
title: 编译器错误 C2467
ms.date: 11/04/2016
f1_keywords:
- C2467
helpviewer_keywords:
- C2467
ms.assetid: f9ead270-5d0b-41cc-bdcd-586a647c67a7
ms.openlocfilehash: aa45cbb19519dea7bd5c8fb96abd2c76ea30a786
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50598007"
---
# <a name="compiler-error-c2467"></a>编译器错误 C2467

非法声明的匿名用户定义的类型

声明用户定义的嵌套的类型。 编译 C 源代码与 ANSI 兼容性选项时，这是一个错误 ([/Za](../../build/reference/za-ze-disable-language-extensions.md)) 启用。

下面的示例生成 C2467:

```
//C2467.c
// compile with: /Za
int main() {
   struct X {
      union { int i; };   // C2467, nested declaration
   };
}
```