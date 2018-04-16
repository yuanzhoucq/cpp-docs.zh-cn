---
title: "链接输入文件 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- link
dev_langs:
- C++
helpviewer_keywords:
- files [C++], LINK
- module definition files
- resources [C++], linker files
- LINK tool [C++], input files
- module definition files, linker files
- input files [C++], LINK
- linker [C++], input files
- import libraries [C++], linker files
- command input to linker files [C++]
ms.assetid: bb26fcc5-509a-4620-bc3e-b6c6e603a412
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1d0cae9498d2c9b49e52cf56991d2425de39d7e1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="link-input-files"></a>LINK 输入文件
链接器提供包含对象、 导入和标准库、 资源、 模块定义和输入的命令的文件。 链接不使用文件扩展名来做出假设文件的内容。 相反，LINK 检查每个输入的文件，以确定它是什么类型的文件。  
  
 在命令行上的对象文件中命令行显示的顺序处理。 库以及，按照从命令行顺序搜索以下需要注意： 是的符号无法解析时将在库中的对象文件中搜索在该库中第一次，然后从命令行和以下库[/DEFAULTLIB （指定默认库）](../../build/reference/defaultlib-specify-default-library.md)指令，然后到命令行的开头的所有库。  
  
> [!NOTE]
>  链接不再接受分号 （或任何其他字符） 作为响应文件和顺序文件中的注释的开头。 分号仅被识别为模块定义文件 (.def) 中的注释的开始。  
  
 链接使用以下类型的输入文件：  
  
-   [.obj 文件](../../build/reference/dot-obj-files-as-linker-input.md)  
  
-   [.netmodule 文件](../../build/reference/netmodule-files-as-linker-input.md)  
  
-   [.lib 文件](../../build/reference/dot-lib-files-as-linker-input.md)  
  
-   [.exp 文件](../../build/reference/dot-exp-files-as-linker-input.md)  
  
-   [.def 文件](../../build/reference/dot-def-files-as-linker-input.md)  
  
-   [.pdb 文件](../../build/reference/dot-pdb-files-as-linker-input.md)  
  
-   [.res 文件](../../build/reference/dot-res-files-as-linker-input.md)  
  
-   [.exe 文件](../../build/reference/dot-exe-files-as-linker-input.md)  
  
-   [.txt 文件](../../build/reference/dot-txt-files-as-linker-input.md)  
  
-   [.ilk 文件](../../build/reference/dot-ilk-files-as-linker-input.md)  
  
## <a name="see-also"></a>请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)