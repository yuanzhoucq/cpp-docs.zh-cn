---
title: 编译器错误 C2467
ms.date: 11/04/2016
f1_keywords:
- C2467
helpviewer_keywords:
- C2467
ms.assetid: f9ead270-5d0b-41cc-bdcd-586a647c67a7
ms.openlocfilehash: da17a3f78c8cab8144cb66b9a672dc59190b50f9
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301140"
---
# <a name="compiler-error-c2467"></a>编译器错误 C2467

匿名 "用户定义类型" 的声明非法

已声明嵌套的用户定义类型。 这是在启用 ANSI 兼容性选项（[/za](../../build/reference/za-ze-disable-language-extensions.md)）的情况下编译 C 源代码时出错。

下面的示例生成 C2467：

```c
//C2467.c
// compile with: /Za
int main() {
   struct X {
      union { int i; };   // C2467, nested declaration
   };
}
```
