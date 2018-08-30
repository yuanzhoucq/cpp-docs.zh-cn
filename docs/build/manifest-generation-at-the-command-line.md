---
title: 命令行上的清单生成 |Microsoft Docs
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
ms.openlocfilehash: 97e2bb423deb4a50da0cf0772ae81e19bb4b48eb
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43220722"
---
# <a name="manifest-generation-at-the-command-line"></a>命令行上的清单生成
在生成 C/c + + 应用程序从命令行使用 nmake 或类似工具时，链接器已处理所有对象文件和生成最终二进制文件之后，将生成的清单。 链接器收集程序集信息存储在对象文件，并将组合到最终的清单文件的此信息。 默认情况下链接器将生成名为的文件 < 二进制 >。\<扩展 >.manifest 来描述最终二进制文件。 链接器不会嵌入二进制文件中的清单文件，仅可以生成为外部文件的清单。 有几种方法来将最终二进制文件，例如，使用清单嵌入[清单工具 (mt.exe)](https://msdn.microsoft.com/library/aa375649)或编译成资源文件的清单。 务必记住，特定的规则需要时最终二进制文件中，若要启用增量链接等功能将清单嵌入遵循签名，以及编辑并继续。 在讨论这些和其他选项[如何： 将嵌入清单内 C/c + + 应用程序一](../build/how-to-embed-a-manifest-inside-a-c-cpp-application.md)时在命令行上生成。  
  
## <a name="see-also"></a>请参阅  
 [清单](https://msdn.microsoft.com/library/aa375365)   
 [/INCREMENTAL （增量链接）](../build/reference/incremental-link-incrementally.md)   
 [强名称程序集 （程序集签名） (C + + CLI)](../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md)   
 [编辑并继续](/visualstudio/debugger/edit-and-continue)   
 [了解 C/C++ 程序的清单生成](../build/understanding-manifest-generation-for-c-cpp-programs.md)