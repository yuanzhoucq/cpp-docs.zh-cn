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
ms.openlocfilehash: f0c0d9a4e5e5f52d239f1a8591006b3d9e369778
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/06/2019
ms.locfileid: "70740111"
---
# <a name="zcinline-remove-unreferenced-comdat"></a>/Zc:inline（移除未引用的 COMDAT）

移除为 COMDAT 或只具有内部链接的未引用函数或数据。 指定 **/zc： inline**后，编译器要求使用内联数据或内联函数的翻译单元也必须包含数据或函数的定义。

## <a name="syntax"></a>语法

> **/Zc:inline**[ **-** ]

## <a name="remarks"></a>备注

指定 **/zc： inline**后，编译器不会为未引用的 COMDAT 函数或数据发出符号信息，也不会为仅具有内部链接的函数或数据发出符号信息。 此优化简化了发布版本中的链接器执行的某些工作，或在指定链接器选项[/opt： REF](opt-optimizations.md)时执行的工作。 编译器执行此优化后，可显著减小 .obj 文件大小并提高链接器速度。 如果已禁用优化（[/od](od-disable-debug.md)）或指定了[/Gl （全程序优化）](gl-whole-program-optimization.md) ，则不启用此编译器选项。

默认情况下，在命令行生成中，此选项处于关闭状态（ **/zc： inline**）。 [/Permissive-](permissive-standards-conformance.md)选项不启用 **/zc： inline**。 在 MSBuild 项目中，选项由**配置属性** >  > **C/C++** **语言** > "**删除未引用的代码和数据**属性" 设置，该属性设置为 **"是"** 。缺省值.

如果指定了 **/zc： inline** ，则编译器强制执行 c + + 11 要求，如果`inline`所声明的所有函数都必须具有相同翻译单元中可用的定义，则为。 如果未指定选项，则 Microsoft 编译器允许不符合标准的代码，该代码可调用`inline`即使没有可见定义也声明的函数。 有关详细信息，请参阅 3.2 节和 7.1.2 节中的 C++11 标准。 Visual Studio 2013 Update 2 中引入了此编译器选项。

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

void main() {
   Example example;
   example.inline_call(); // normal call when definition unavailable
}
```

当 **/zc： inline**处于启用状态时，相同的代码会导致[LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md)错误，因为编译器不会`Example::inline_call`在示例 .obj 中发出非内联代码体。这会导致 `main` 中的非内联调用以引用未定义的外部符号。

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

void main() {
   Example2 example2;
   example2.inline_call(); // normal call when definition unavailable
}
```

有关 Visual C++ 中一致性问题的详细信息，请参阅 [Nonstandard Behavior](../../cpp/nonstandard-behavior.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页” 对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 选择 "**配置属性** > " " > **C/C++** **语言**" 属性页。

1. 修改 "**删除未引用的代码和数据**" 属性，然后选择 **"确定"** 。

## <a name="see-also"></a>请参阅

[/Zc（一致性）](zc-conformance.md)<br/>
