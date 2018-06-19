---
title: .用作链接器输入 lib 文件 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.AdditionalDependencies
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8382e43398c4b6e5241542e6b41fdee8e2f70eff
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32374539"
---
# <a name="lib-files-as-linker-input"></a>用作链接器输入的 .Lib 文件
链接接受 COFF 标准库和 COFF 导的入库，这两种通常具有扩展名。 lib。 标准库包含对象，并且通过 LIB 工具创建。 导入库包含有关其他程序中导出的信息和链接通过它生成包含导出的程序时或通过创建 LIB 工具。 有关使用 LIB 创建标准或导入库的信息，请参阅[LIB 引用](../../build/reference/lib-reference.md)。 有关使用链接来创建导入库的详细信息，请参阅[/DLL](../../build/reference/dll-build-a-dll.md)选项。  
  
库链接到指定为文件的名称自变量或默认库。 链接通过在命令行上指定的库中的第一次搜索解析外部引用，然后在指定的默认库与[/DEFAULTLIB](../../build/reference/defaultlib-specify-default-library.md)选项，且然后默认库名为在.obj 文件中。 如果使用的库名称指定路径，链接查找该目录中的库。 如果未指定路径，则链接查找第一个链接，正在运行的目录中，然后在 LIB 环境变量中指定任何目录中。  
  
## <a name="to-add-lib-files-as-linker-input-in-the-development-environment"></a>要添加为在开发环境中的链接器输入的.lib 文件  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  选择**输入**中的属性页**链接器**文件夹。  
  
3.  修改**附加依赖项**要添加的.lib 文件属性。  
  
## <a name="to-programmatically-add-lib-files-as-linker-input"></a>若要以编程方式添加用作链接器输入的.lib 文件  
  
-   请参阅[AdditionalDependencies](https://msdn.microsoft.com/library/microsoft.visualstudio.vcprojectengine.vclinkertool.additionaldependencies.aspx)。  
  
## <a name="example"></a>示例  
下面的示例演示如何生成和使用.lib 文件。 首先，生成的.lib 文件：  
  
```cpp  
// lib_link_input_1.cpp  
// compile by using: cl /LD lib_link_input_1.cpp  
__declspec(dllexport) int Test() {  
   return 213;  
}  
```  
  
然后，通过使用刚刚创建的.lib 文件编译此示例：  
  
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
 [LINK 输入的文件](../../build/reference/link-input-files.md)   
 [链接器选项](../../build/reference/linker-options.md)