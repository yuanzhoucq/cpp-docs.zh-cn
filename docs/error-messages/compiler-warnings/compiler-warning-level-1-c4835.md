---
title: 编译器警告 （等级 1） C4835 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4835
dev_langs:
- C++
helpviewer_keywords:
- C4835
ms.assetid: d2e44c62-7b0e-4a45-943d-97903e27ed9d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 70492be13d312c5d167990cfa0b6c0d741e1055f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46080098"
---
# <a name="compiler-warning-level-1-c4835"></a>编译器警告（等级 1）C4835

variable： 在主机程序集中首次执行托管的代码之后，将不会运行导出的数据的初始值设定项

在访问托管组件之间的数据时，建议不使用本机 c + + 导入和导出机制。 相反，声明在托管类型的内部数据成员，并引用元数据与`#using`客户端中。 有关详细信息，请参阅 [#using 指令](../../preprocessor/hash-using-directive-cpp.md)。

## <a name="example"></a>示例

下面的示例生成 C4835。

```
// C4835.cpp
// compile with: /W1 /clr /LD
int f() { return 1; }
int n = 9;

__declspec(dllexport) int m = f();   // C4835
__declspec(dllexport) int *p = &n;   // C4835
```

## <a name="example"></a>示例

下面的示例使用在上一示例中，显示这些变量的值不按预期方式构建的组件。

```
// C4835_b.cpp
// compile with: /clr C4835.lib
#include <stdio.h>
__declspec(dllimport) int m;
__declspec(dllimport) int *p;

int main() {
   printf("%d\n", m);
   printf("%d\n", p);
}
```

```Output
0
268456008
```