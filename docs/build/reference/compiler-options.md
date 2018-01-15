---
title: "编译器选项 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- cl.exe compiler
- IPF Visual C++ compiler
- Itanium Visual C++ compiler
- compiler options, C++
- x64 Visual C++ compiler
ms.assetid: ed3376c8-bef4-4c9a-80e9-3b5da232644c
caps.latest.revision: "18"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c433abea04ff81c69fe1b73569ea7e043e6e81ac
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-options"></a>编译器选项
cl.exe 是控制对 Microsoft C 和 c + + 编译器和链接器工具。 cl.exe 可以仅在 Microsoft Visual Studio 支持的操作系统上运行。  
  
> [!NOTE]
>  你只能从 [!INCLUDE[vsprvs](../../assembler/masm/includes/vsprvs_md.md)] 命令提示符启动此工具。 不能从系统命令提示符或从文件资源管理器启动此工具。  
  
 编译器生成通用对象文件格式 (COFF) 对象 (.obj) 文件。 链接器生成可执行文件 (.exe) 文件或动态链接库 (Dll)。  
  
 请注意，所有编译器选项都都区分大小写。  
  
 若要编译链接的情况下，使用[/c](../../build/reference/c-compile-without-linking.md)。  
  
## <a name="finding-an-option"></a>查找选项  
 若要查找特定的编译器选项，请参阅以下列表之一：  
  
-   [按字母顺序列出的编译器选项](../../build/reference/compiler-options-listed-alphabetically.md)  
  
-   [按类别列出的编译器选项](../../build/reference/compiler-options-listed-by-category.md)  
  
## <a name="specifying-options"></a>指定选项  
 每个编译器选项的主题讨论如何可以在开发环境中设置它。 指定在开发环境外的选项的信息，请参阅：  
  
-   [编译器命令行语法](../../build/reference/compiler-command-line-syntax.md)  
  
-   [CL 命令文件](../../build/reference/cl-command-files.md)  
  
-   [CL 环境变量](../../build/reference/cl-environment-variables.md)  
  
## <a name="related-build-tools"></a>相关的生成工具  
 使用[NMAKE](../../build/nmake-reference.md)生成输出文件。  
  
 使用[BSCMAKE](../../build/reference/bscmake-reference.md)以支持类浏览。  
  
 [链接器选项](../../build/reference/linker-options.md)也会影响程序的生成方式。  
  
## <a name="see-also"></a>请参阅  
 [C/C++ 生成参考](../../build/reference/c-cpp-building-reference.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)   
 [快速编译](../../build/reference/fast-compilation.md)   
 [CL 调用链接器](../../build/reference/cl-invokes-the-linker.md)