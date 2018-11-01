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
ms.openlocfilehash: e8d2a97e4d887b914d15871ce1679c95cc3cda97
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50452723"
---
# <a name="function-inlining-problems"></a>函数内联问题

如果使用函数内联，则必须：

- 已在包含的标头文件中实现的内联函数。

- 具有内联打开标头文件中。

```
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

```
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

如果使用的`#pragma inline_depth`编译器指令，请确保你已设置的值为 2 或更高版本。 值为零将关闭内联。 此外请确保你使用 **/ob1**或 **/ob2**编译器选项。

混合使用不同的模块上的内联和非内联编译选项有时会导致问题。 如果使用函数内联开启创建 c + + 库 ([/ob1](../../build/reference/ob-inline-function-expansion.md)或[/ob2](../../build/reference/ob-inline-function-expansion.md))，但相应的头文件描述函数具有内联关闭 （没有选项），你将收到错误 LNK2001。 函数执行不内联到代码从文件中获取标头，但由于它们不是库文件中没有地址来解析引用。

同样，使用函数内联的项目尚未定义的函数的.cpp 文件中而不是标头中，文件还将获得 LNK2019。 标头文件是包含无处不在认为合适，但函数才是内联在.cpp 文件中通过通过编译器;因此，链接器将函数视为未解析的外部对象时在其他模块中使用。

```
// LNK2019_FIP.h
struct testclass {
   void PublicStatMemFunc1(void);
};
```

然后

```
// LNK2019_FIP.cpp
// compile with: /c
#include "LNK2019_FIP.h"
inline void testclass::PublicStatMemFunc1(void) {}
```

然后

```
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

## <a name="see-also"></a>请参阅

[链接器工具错误 LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md)