---
title: 编译器警告（等级 1）C4835
ms.date: 11/04/2016
f1_keywords:
- C4835
helpviewer_keywords:
- C4835
ms.assetid: d2e44c62-7b0e-4a45-943d-97903e27ed9d
ms.openlocfilehash: 0427a97a9e368a19a40a8d1a552f7713e36f831e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62380846"
---
# <a name="compiler-warning-level-1-c4835"></a>编译器警告（等级 1）C4835

variable： 在主机程序集中首次执行托管的代码之后，将不会运行导出的数据的初始值设定项

在访问托管组件之间的数据时，建议您不要使用本机C++导入和导出机制。 相反，声明在托管类型的内部数据成员，并引用元数据与`#using`客户端中。 有关详细信息，请参阅 [#using 指令](../../preprocessor/hash-using-directive-cpp.md)。

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