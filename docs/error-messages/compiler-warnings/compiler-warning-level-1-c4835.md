---
title: 编译器警告（等级 1）C4835
ms.date: 11/04/2016
f1_keywords:
- C4835
helpviewer_keywords:
- C4835
ms.assetid: d2e44c62-7b0e-4a45-943d-97903e27ed9d
ms.openlocfilehash: f86fcaea8a742c19ce175a453c06669178ed2145
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80174851"
---
# <a name="compiler-warning-level-1-c4835"></a>编译器警告（等级 1）C4835

"variable"：在主机程序集中首次执行托管代码时，导出数据的初始值设定项将不会运行

访问托管组件之间的数据时，建议不要使用本机C++导入和导出机制。 相反，请在托管类型内声明数据成员，并在客户端中使用 `#using` 引用元数据。 有关详细信息，请参阅 [#using 指令](../../preprocessor/hash-using-directive-cpp.md)。

## <a name="example"></a>示例

下面的示例生成 C4835。

```cpp
// C4835.cpp
// compile with: /W1 /clr /LD
int f() { return 1; }
int n = 9;

__declspec(dllexport) int m = f();   // C4835
__declspec(dllexport) int *p = &n;   // C4835
```

## <a name="example"></a>示例

下面的示例使用上一示例中生成的组件，并显示变量的值与预期不符。

```cpp
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
