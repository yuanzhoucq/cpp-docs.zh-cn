---
title: 函数内联问题
ms.date: 11/04/2016
helpviewer_keywords:
- /Ob1 C++ compiler option
- inline functions, problems
- -Ob1 C++ compiler option
- /Ob2 C++ compiler option
- -Ob2 C++ compiler option
- function inlining problems
ms.assetid: 65d59943-4b3c-4a43-aeb6-dccbf7686740
ms.openlocfilehash: cb4653bd2f03683b9abad1eea0e9ffa88222090e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80184237"
---
# <a name="function-inlining-problems"></a>函数内联问题

如果你使用的是函数内联，则必须：

- 在包含的头文件中实现内联函数。

- 在头文件中打开了内联。

```cpp
// LNK2019_function_inline.cpp
// compile with: /c
// post-build command: lib LNK2019_function_inline.obj
#include <stdio.h>
struct _load_config_used {
   void Test();
   void Test2() { printf("in Test2\n"); }
};

void _load_config_used::Test() { printf("in Test\n"); }
```

然后，

```cpp
// LNK2019_function_inline_2.cpp
// compile with: LNK2019_function_inline.lib
struct _load_config_used {
   void Test();
   void Test2();
};

int main() {
   _load_config_used x;
   x.Test();
   x.Test2();   // LNK2019
}
```

如果使用 `#pragma inline_depth` 编译器指令，请确保设置的值为2或更大。 如果值为零，则将关闭内联。 此外，请确保使用的是 **/Ob1**或 **/Ob2**编译器选项。

在不同模块上混合内联和非内联编译选项有时会导致问题。 如果创建C++库时启用了函数内联（[/Ob1](../../build/reference/ob-inline-function-expansion.md)或[/Ob2](../../build/reference/ob-inline-function-expansion.md)），但描述函数的相应标头文件启用了内联（无选项），则会出现错误 LNK2001。 函数不会从头文件中内联到代码中，但由于它们不在库文件中，因此没有用于解析引用的地址。

同样，使用函数内联的项目还在 .cpp 文件而不是头文件中定义函数也会获得 LNK2019。 标头文件被视为适当的位置，但仅当 .cpp 文件通过编译器时才会内联函数;因此，在其他模块中使用时，链接器将函数视为未解析的外部函数。

```cpp
// LNK2019_FIP.h
struct testclass {
   void PublicStatMemFunc1(void);
};
```

然后

```cpp
// LNK2019_FIP.cpp
// compile with: /c
#include "LNK2019_FIP.h"
inline void testclass::PublicStatMemFunc1(void) {}
```

然后

```cpp
// LNK2019_FIP_2.cpp
// compile with: LNK2019_FIP.cpp
// LNK2019 expected
#include "LNK2019_FIP.h"
int main() {
   testclass testclsObject;

   // module cannot see the implementation of PublicStatMemFunc1
   testclsObject.PublicStatMemFunc1();
}
```

## <a name="see-also"></a>另请参阅

[链接器工具错误 LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md)
