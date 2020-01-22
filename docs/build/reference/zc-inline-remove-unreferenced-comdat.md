---
title: /Zc:inline（移除未引用的 COMDAT）
ms.date: 09/05/2019
f1_keywords:
- /Zc:inline
- VC.Project.VCCLCompilerTool.RemoveUnreferencedCodeData
helpviewer_keywords:
- -Zc compiler options (C++)
- /Zc compiler options (C++)
- Zc compiler options (C++)
- /Zc:inline
ms.assetid: a4c94224-1d73-4bea-a9d5-4fa73dc924df
ms.openlocfilehash: 42791b2e337fb9a9724a165145e757152b8d679d
ms.sourcegitcommit: a930a9b47bd95599265d6ba83bb87e46ae748949
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/22/2020
ms.locfileid: "76518239"
---
# <a name="zcinline-remove-unreferenced-comdat"></a>/Zc:inline（移除未引用的 COMDAT）

删除未引用的数据或 Comdat 的或仅具有内部链接的函数。 在 **/zc： inline**下，编译器指定包含内联数据或函数的翻译单元也必须包含它们的定义。

## <a name="syntax"></a>语法

> **/Zc:inline**[ **-** ]

## <a name="remarks"></a>备注

指定 **/zc： inline**后，编译器不会为未引用的 COMDAT 函数或数据发出符号信息。 或者，对于仅具有内部链接的数据或函数。 此优化简化了链接器在发布版本中进行的某些工作，或指定了[/opt： REF](opt-optimizations.md)链接器选项。 此编译器优化可显著减少 .obj 文件大小并提高链接器的速度。 禁用优化（[/od](od-disable-debug.md)）时编译器选项未启用。 指定为[/gl （全程序优化）](gl-whole-program-optimization.md)时。

默认情况下，在命令行生成中，此选项处于关闭状态（ **/zc： inline**）。 [/Permissive-](permissive-standards-conformance.md)选项不启用 **/zc： inline**。 在 MSBuild 项目中，选项由**配置属性**设置 > **C++ C/**  > **语言** > 删除未**引用的代码和数据**属性，默认情况下，该属性设置为 **"是"** 。

如果指定了 **/zc： inline** ，则编译器强制执行 c + + 11 要求，如果使用 `inline` 声明的所有函数，则这些函数必须在使用时具有相同翻译单元中可用的定义。 如果未指定选项，则 Microsoft 编译器允许不符合的代码调用 `inline` 声明的函数，即使没有可见的定义也是如此。 有关详细信息，请参阅 3.2 节和 7.1.2 节中的 C++11 标准。 Visual Studio 2013 Update 2 中引入了此编译器选项。

若要使用 **/zc： inline**选项，请更新不兼容的代码。

此示例演示当使用默认 **/zc： inline**选项时，不符合定义的内联函数声明的不符合使用情况仍会进行编译和链接：

```cpp
// example.h
// Compile by using: cl /W4 /EHsc /O2 zcinline.cpp example.cpp
#pragma once

class Example {
public:
   inline void inline_call(); // declared but not defined inline
   void normal_call();
   Example() {};
};
```

```cpp
// example.cpp
// Compile by using: cl /W4 /EHsc /O2 zcinline.cpp example.cpp
#include <stdio.h>
#include "example.h"

void Example::inline_call() {
   printf("inline_call was called.\n");
}

void Example::normal_call() {
   printf("normal_call was called.\n");
   inline_call(); // with /Zc:inline-, inline_call forced into .obj file
}
```

```cpp
// zcinline.cpp
// Compile by using: cl /W4 /EHsc /O2 zcinline.cpp example.cpp
#include "example.h"

int main() {
   Example example;
   example.inline_call(); // normal call when definition unavailable
}
```

当 **/zc： inline**处于启用状态时，相同的代码会导致[LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md)错误，因为编译器不会为示例 .obj 中的 `Example::inline_call` 发出非内联代码体。这会导致 `main` 中的非内联调用引用未定义的外部符号。

若要解决此错误，可从 `inline` 的声明中移除 `Example::inline_call` 关键字、将 `Example::inline_call` 的定义移到头文件中，或将 `Example` 的实现移到 main.cpp 中。 下一个示例将定义移到头文件中，其中该定义对包含该头文件的所有调用方都可见。

```cpp
// example2.h
// Compile by using: cl /W4 /EHsc /O2 zcinline2.cpp example2.cpp
#pragma once
#include <stdio.h>

class Example2 {
public:
   inline void inline_call() {
      printf("inline_call was called.\n");
   }
   void normal_call();
   Example2() {};
};
```

```cpp
// example2.cpp
// Compile by using: cl /W4 /EHsc /O2 zcinline2.cpp example2.cpp
#include "example2.h"

void Example2::normal_call() {
   printf("normal_call was called.\n");
   inline_call();
}
```

```cpp
// zcinline2.cpp
// Compile by using: cl /W4 /EHsc /O2 zcinline2.cpp example2.cpp
#include "example2.h"

int main() {
   Example2 example2;
   example2.inline_call(); // normal call when definition unavailable
}
```

有关 Visual C++ 中一致性问题的详细信息，请参阅 [Nonstandard Behavior](../../cpp/nonstandard-behavior.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页” 对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 选择 "**配置属性**" > **CC++ /**  > **语言**"属性页。

1. 修改 "**删除未引用的代码和数据**" 属性，然后选择 **"确定"** 。

## <a name="see-also"></a>另请参阅

[/Zc（一致性）](zc-conformance.md)<br/>
