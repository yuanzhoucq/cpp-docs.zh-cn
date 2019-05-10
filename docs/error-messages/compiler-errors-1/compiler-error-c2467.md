---
title: 编译器错误 C2467
ms.date: 11/04/2016
f1_keywords:
- C2467
helpviewer_keywords:
- C2467
ms.assetid: f9ead270-5d0b-41cc-bdcd-586a647c67a7
ms.openlocfilehash: aa45cbb19519dea7bd5c8fb96abd2c76ea30a786
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62302080"
---
# <a name="compiler-error-c2467"></a>编译器错误 C2467

illegal declaration of anonymous 'user-defined-type'

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