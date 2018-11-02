---
title: 如何： 检测-clr 编译
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- compilation, detecting /clr
- /clr compiler option [C++], detecting use of
ms.assetid: a9310045-4810-4637-a64a-0b31a08791c1
ms.openlocfilehash: 600c74bfda6673295269902021afcecd95b90077
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50590822"
---
# <a name="how-to-detect-clr-compilation"></a>如何：检测 /clr 编译

使用`_MANAGED`或`_M_CEE`宏以查看是否使用编译的模块 **/clr**。 有关详细信息，请参阅 [/clr（公共语言运行时编译）](../build/reference/clr-common-language-runtime-compilation.md)。

有关宏的详细信息，请参阅[预定义的宏](../preprocessor/predefined-macros.md)。

## <a name="example"></a>示例

```
// detect_CLR_compilation.cpp
// compile with: /clr
#include <stdio.h>

int main() {
   #if (_MANAGED == 1) || (_M_CEE == 1)
      printf_s("compiling with /clr\n");
   #else
      printf_s("compiling without /clr\n");
   #endif
}
```

## <a name="see-also"></a>请参阅

[使用 C++ 互操作（隐式 PInvoke）](../dotnet/using-cpp-interop-implicit-pinvoke.md)