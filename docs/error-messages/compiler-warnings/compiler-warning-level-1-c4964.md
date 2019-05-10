---
title: 编译器警告（等级 1）C4964
ms.date: 11/04/2016
f1_keywords:
- C4964
helpviewer_keywords:
- C4964
ms.assetid: b89c9274-8a92-4b7c-aa30-3fbb1b68ac73
ms.openlocfilehash: 556c6e0963fc41d76cd123373cc4cd85edc66962
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62384135"
---
# <a name="compiler-warning-level-1-c4964"></a>编译器警告（等级 1）C4964

未不指定任何优化选项;将不会收集个人资料信息

[/GL](../../build/reference/gl-whole-program-optimization.md)并[/LTCG](../../build/reference/ltcg-link-time-code-generation.md)已指定，但没有优化请求，因此会生成任何.pgc 文件，并因此，不按配置优化将会成为现实。

如果你想要运行应用程序时生成的.pgc 文件，指定之一[/O](../../build/reference/o-options-optimize-code.md)编译器选项。

下面的示例生成 C4964:

```
// C4964.cpp
// compile with: /W1 /GL /link /ltcg:pgi
// C4964 expected
// Add /O2, for example, to the command line to resolve this warning.
int main() {
   int i;
}
```