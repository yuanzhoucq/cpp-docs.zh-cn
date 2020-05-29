---
title: 编译器警告（等级 1）C4964
ms.date: 11/04/2016
f1_keywords:
- C4964
helpviewer_keywords:
- C4964
ms.assetid: b89c9274-8a92-4b7c-aa30-3fbb1b68ac73
ms.openlocfilehash: 7852340bc056e126238a2d9c7493887ef3caf93e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80174487"
---
# <a name="compiler-warning-level-1-c4964"></a>编译器警告（等级 1）C4964

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
