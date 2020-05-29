---
title: 命令行上的清单生成
ms.date: 11/04/2016
helpviewer_keywords:
- manifests [C++]
- manifest tool (mt.exe)
ms.assetid: fc2ff255-82b1-4c44-af76-8405c5850292
ms.openlocfilehash: 381406213422e286dd9aba26adcdbd6caff7bfe3
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69493195"
---
# <a name="manifest-generation-at-the-command-line"></a>命令行上的清单生成

使用 nmake 或类似工具从命令行生成 C/C++ 应用程序时，会在链接器处理所有对象文件并生成最终二进制文件后生成清单。 链接器收集存储在对象文件中的程序集信息，并将此信息合并到最终清单文件中。 默认情况下，链接器将生成一个名为 binary_name.extension.manifest 的文件，用于描述最终二进制文件   。 链接器不会将清单文件嵌入到二进制文件中，只能将清单作为外部文件来生成。 有几种方法可以将清单嵌入到最终二进制文件中，如使用[清单工具 (mt.exe)](/windows/win32/sbscs/mt-exe) 或将清单编译到资源文件中。 请务必记住，将清单嵌入到最终二进制文件中时，必须遵循特定规则才能启用增量链接、签名、编辑和继续等功能。 如需了解如何在命令行上生成这些选项和其他选项，请参阅[如何：将清单嵌入到 C/C++ 应用程序中](how-to-embed-a-manifest-inside-a-c-cpp-application.md)。

## <a name="see-also"></a>请参阅

[清单](/windows/win32/sbscs/manifests)<br/>
[/INCREMENTAL（增量链接）](reference/incremental-link-incrementally.md)<br/>
[强名称程序集（程序集签名）(C++/CLI)](../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md)<br/>
[编辑并继续](/visualstudio/debugger/edit-and-continue)<br/>
[了解 C/C++ 程序的清单生成](understanding-manifest-generation-for-c-cpp-programs.md)<br/>
