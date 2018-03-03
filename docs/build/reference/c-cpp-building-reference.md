---
title: "C/c + + 生成参考 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- compiling source code [C++], additional information
- cl.exe compiler [C++], building programs
- linker [C++], building reference
- builds [C++], additional information
ms.assetid: 100b4ccf-572c-4d1f-970c-fa0bc0cc0d2d
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9e2269be27dd039357c11d38a2be83b5fc9d6504
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="cc-building-reference"></a>C/C++ 生成参考
Visual c + + 提供生成 C/c + + 程序的两种的方法。 最简单的 （也是最常见的） 的方法是[Visual c + + 开发环境中生成](../../ide/building-cpp-projects-in-visual-studio.md)。 另一种方法是[从命令提示符使用命令行工具生成](../../build/building-on-the-command-line.md)。 在任一情况下，你可以创建使用 Visual c + + 源代码编辑器或第三方编辑器所选的源文件。  
  
 如果程序使用生成文件，而不是.vcxproj 文件，则仍可以生成它在开发环境中作为[外部项目](../../ide/building-external-projects.md)。  
  
## <a name="in-this-section"></a>本节内容  
 [编译 C/C++ 程序](../../build/reference/compiling-a-c-cpp-program.md)  
 描述的编译器，创建一个包含机器代码、 链接器指令、 节、 外部引用和函数/数据名称的对象文件。  
  
 [链接](../../build/reference/linking.md)  
 描述链接器合并代码从由编译器创建的对象文件和静态链接的库，解析的名称引用，并创建可执行文件。  
  
 [发行版本](../../build/reference/release-builds.md)  
 提供有关原因和时间你想要更改从调试版本为发布版本，并还讨论一些从调试版本更改为发布版本时可能遇到的问题。  
  
 [优化代码](../../build/reference/optimizing-your-code.md)  
 提供指向主题的主题讨论为优化代码的机制：  
  
 [C/C++ 生成工具](../../build/reference/c-cpp-build-tools.md)  
 提供以下命令行工具来查看或操作生成输出：  
  
 [C/C++ 生成错误](../../error-messages/compiler-errors-1/c-cpp-build-errors.md)  
 引入了内容表中的生成错误部分。  
  
## <a name="related-sections"></a>相关章节  
 [C/C++ 预处理器参考](../../preprocessor/c-cpp-preprocessor-reference.md)  
 讨论预处理器，准备编译器通过翻译宏、 运算符和指令的源文件。  
  
 [了解自定义生成步骤和生成事件](../../ide/understanding-custom-build-steps-and-build-events.md)  
 探讨如何自定义生成过程。  
  
 [生成 C/c + + 程序](../../build/building-c-cpp-programs.md)  
 提供一些链接，它们指向描述如何从命令行或 Visual Studio 的集成开发环境构建程序的主题。  
  
 [设置编译器选项](../../build/reference/setting-compiler-options.md)  
 描述如何在开发环境中或在命令行上设置编译器选项。  
  
 [编译器选项](../../build/reference/compiler-options.md)  
 提供指向探讨如何使用编译器选项的主题。  
  
 [设置链接器选项](../../build/reference/setting-linker-options.md)  
 描述如何设置链接器选项内部或外部集成的开发环境。  
  
 [链接器选项](../../build/reference/linker-options.md)  
 提供指向探讨如何使用链接器选项的主题。  
  
 [BSCMAKE 参考](../../build/reference/bscmake-reference.md)  
 描述 Microsoft 浏览信息维护实用工具 (BSCMAKE。EXE)，哪些从.sbr 生成浏览信息文件 (.bsc) 在编译期间创建的文件。  
  
 [LIB 引用](../../build/reference/lib-reference.md)  
 介绍 Microsoft 库管理器 (LIB.exe)，它用于创建和管理通用对象文件格式 (COFF) 对象文件的库。  
  
 [EDITBIN 参考](../../build/reference/editbin-reference.md)  
 描述 Microsoft COFF 二进制文件编辑器 (EDITBIN。EXE)，其中修改通用对象文件格式 (COFF) 的二进制文件。  
  
 [DUMPBIN 参考](../../build/reference/dumpbin-reference.md)  
 描述 Microsoft COFF 二进制文件转储器 (DUMPBIN。EXE)，它会显示有关通用对象文件格式 (COFF) 的二进制文件的信息。  
  
 [NMAKE 参考](../../build/nmake-reference.md)  
 描述 Microsoft 程序维护实用工具 (NMAKE。EXE)，它是一种工具生成的项目，根据描述文件中包含的命令。