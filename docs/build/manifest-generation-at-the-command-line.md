---
title: 清单在命令行生成 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- manifests [C++]
- manifest tool (mt.exe)
ms.assetid: fc2ff255-82b1-4c44-af76-8405c5850292
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7f740030e48a33284a31da4ebd46f0c4d7b6ac7e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="manifest-generation-at-the-command-line"></a>命令行上的清单生成
在生成 C/c + + 应用程序从命令行使用 nmake 或类似的工具时，链接器已处理所有对象文件和生成最终二进制文件后，将生成的清单。 链接器收集存储在对象文件中的程序集信息，再将合并到最终的清单文件的此信息。 默认情况下，链接器将生成名为的文件 < 于二进制文件名 >。\<扩展 >.manifest 用于描述最终二进制文件。 链接器不会嵌入二进制文件的清单文件，并可以仅生成为外部文件的清单。 有几种方法来将最终二进制文件，例如，使用清单嵌入[清单工具 (mt.exe)](http://msdn.microsoft.com/library/aa375649)或编译到一个资源文件的清单。 务必记住，特定的规则必须在最终二进制文件中，若要启用增量链接，诸如功能将清单嵌入时遵循签名，并编辑并继续。 中讨论了这些和其他选项[How to： 嵌入清单内 C/c + + 应用程序](../build/how-to-embed-a-manifest-inside-a-c-cpp-application.md)时在命令行上生成。  
  
## <a name="see-also"></a>请参阅  
 [清单](http://msdn.microsoft.com/library/aa375365)   
 [/INCREMENTAL （增量链接）](../build/reference/incremental-link-incrementally.md)   
 [强名称程序集 （程序集签名） (C + + /cli CLI)](../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md)   
 [编辑并继续](/visualstudio/debugger/edit-and-continue)   
 [了解 C/C++ 程序的清单生成](../build/understanding-manifest-generation-for-c-cpp-programs.md)