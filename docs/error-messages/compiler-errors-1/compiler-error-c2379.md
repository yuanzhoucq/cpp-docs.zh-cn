---
title: 编译器错误 C2379
ms.date: 11/04/2016
f1_keywords:
- C2379
helpviewer_keywords:
- C2379
ms.assetid: 37dc3015-a4af-4341-bbf3-da6150df7e51
ms.openlocfilehash: f096791a6120023e079b93452a4b35c669db2139
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/20/2019
ms.locfileid: "75302102"
---
# <a name="compiler-error-c2379"></a>编译器错误 C2379

提升后，形参号具有不同的类型

指定参数的类型不兼容，因为默认升级使用之前声明中的类型。 这是 ANSI C （[/za](../../build/reference/za-ze-disable-language-extensions.md)）中的错误和 Microsoft 扩展（ **/ze**）的警告。

下面的示例生成 C2379：

```c
// C2379.c
// compile with: /Za
void func();
void func(char);   // C2379, char promotes to int
```
