---
title: 编译器警告（等级1） C4964
ms.date: 11/04/2016
f1_keywords:
- C4964
helpviewer_keywords:
- C4964
ms.assetid: b89c9274-8a92-4b7c-aa30-3fbb1b68ac73
ms.openlocfilehash: 2a75a1b7d3738794046ac697113c3c746bb6fcff
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052245"
---
# <a name="compiler-warning-level-1-c4964"></a>编译器警告（等级1） C4964

未指定优化选项;不会收集配置文件信息

指定了[/gl](../../build/reference/gl-whole-program-optimization.md)和[/ltcg](../../build/reference/ltcg-link-time-code-generation.md) ，但没有请求优化，因此不会生成 pgc 文件，因此不可能进行按配置优化。

如果希望在运行应用程序时生成 pgc 文件，请指定[/o](../../build/reference/o-options-optimize-code.md)编译器选项之一。

下面的示例生成 C4964：

```cpp
// C4964.cpp
// compile with: /W1 /GL /link /ltcg:pgi
// C4964 expected
// Add /O2, for example, to the command line to resolve this warning.
int main() {
   int i;
}
```