---
title: 编译器警告 （等级 1） C4964 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4964
dev_langs:
- C++
helpviewer_keywords:
- C4964
ms.assetid: b89c9274-8a92-4b7c-aa30-3fbb1b68ac73
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7f1644e4603bae36ec9d407294dea78a27e60539
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46086663"
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