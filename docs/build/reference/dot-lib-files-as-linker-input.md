---
title: 用作链接器输入的 .Lib 文件
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.AdditionalDependencies
helpviewer_keywords:
- OMF libraries
- linking [C++], OMF libraries
- import libraries, linker files
- libraries [C++], .lib files as linker input
- COFF files, import libraries
- default libraries [C++], linker output
- default libraries [C++]
- defaults [C++], libraries
- .lib files
ms.assetid: dc5d2b1c-2487-41fa-aa71-ad1e0647958b
ms.openlocfilehash: 0bf791d682b66d9d0da968fb0bfd5229e912e84c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50505337"
---
# <a name="lib-files-as-linker-input"></a>用作链接器输入的 .Lib 文件

链接接受 COFF 标准库和 COFF 导入这两种通常具有扩展名的库。 lib。 标准库包含对象和 LIB 工具创建的。 导入库包含有关在其他程序中导出的信息，并生成包含导出的程序时，或 LIB 工具创建通过链接。 有关使用 LIB 创建标准或导入的库的信息，请参阅[LIB 引用](../../build/reference/lib-reference.md)。 有关使用链接创建导入库的详细信息，请参阅[/DLL](../../build/reference/dll-build-a-dll.md)选项。

一个库链接到指定为文件名称参数或默认库。 链接通过首先在命令行上指定的库中搜索在解析外部引用，然后在指定的默认库与[/DEFAULTLIB](../../build/reference/defaultlib-specify-default-library.md)选项，然后在默认库名为.obj 文件中。 如果使用的库名称指定了路径，链接查找该目录中的库。 如果未指定路径，链接查找第一个链接，正在运行的目录中，然后在 LIB 环境变量中指定的任何目录。

## <a name="to-add-lib-files-as-linker-input-in-the-development-environment"></a>若要添加作为开发环境中的链接器输入的.lib 文件

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 选择**输入**中的属性页**链接器**文件夹。

1. 修改**附加依赖项**要添加的.lib 文件属性。

## <a name="to-programmatically-add-lib-files-as-linker-input"></a>若要以编程方式添加为链接器输入的.lib 文件

- 请参阅[AdditionalDependencies](https://msdn.microsoft.com/library/microsoft.visualstudio.vcprojectengine.vclinkertool.additionaldependencies.aspx)。

## <a name="example"></a>示例

以下示例演示如何生成和使用.lib 文件。 首先，生成的.lib 文件：

```cpp
// lib_link_input_1.cpp
// compile by using: cl /LD lib_link_input_1.cpp
__declspec(dllexport) int Test() {
   return 213;
}
```

并使用刚创建的.lib 文件，然后，编译此示例：

```cpp
// lib_link_input_2.cpp
// compile by using: cl /EHsc lib_link_input_1.lib lib_link_input_2.cpp
__declspec(dllimport) int Test();
#include <iostream>
int main() {
   std::cout << Test() << std::endl;
}
```

```Output
213
```

## <a name="see-also"></a>请参阅

[LINK 输入文件](../../build/reference/link-input-files.md)<br/>
[链接器选项](../../build/reference/linker-options.md)